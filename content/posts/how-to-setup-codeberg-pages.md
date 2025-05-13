+++
title = "How to Setup Codeberg's Pages Server using Docker Compose & Forgejo"
date = "2025-05-12T18:19:54-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "Itsyourdriver"
authorTwitter = "itsyourdriver_" #do not include @
cover = ""
tags = ["hosting", "fun-stuff", "tutorial","ubuntu", "debian", "docker", "homelab"]
keywords = ["static site hosting", "static sites", "github pages", "github pages alternatives", "codeberg pages", "cloudflare pages", "homelab", "docker", "tutorial", "how to setup codeberg pages server", "how to self host static sites"]
description = "This guide goes over how to setup codeberg's pages-server using docker compose, allowing you to provide static site hosting to your forgejo instance."
showFullContent = false
readingTime = true
hideComments = true
+++

If you're like me and deploy/upkeep static sites (this one included) semi-regularly using a generator such as hugo or another, you may have found that there are a few options for hosting said static sites. Whether that's github (where this site is hosted), codeberg (which occasionally has uptime issues), cloudflare pages, statichost.eu, or even sourcehut pages. There are a lot of options. Now what if you could host your static pages, yourself? Well, that's what we're going to do today.

I recently bought a domain for this project, but you'll need one which isn't from a dynamic dns service (unless they let you use wildcard domains & are in the list of supported DNS providers [here](https://go-acme.github.io/lego/dns/#dns-providers).

> ⚠️ This guide doesn't go over how to setup support for custom domains (using a reverse proxy), as I still haven't figured it out yet. If you have (using any reverse proxy), please contact me via any platform that I'm active on (incl. matrix.org, @itsyourdriver_)
>
> This guide is made with my own experience of setting this server up, some practices may be bad or just okay. If something is off, let me know.
>
> **You also need a self-hosted forgejo instance for this guide to work.**

For this guide, I'll be using cloudflare as my DNS provider (to initiate certificates), you can use any of the ones listed [here](https://go-acme.github.io/lego/dns/#dns-providers)

This guide will be using a VPS, as my homelab already has ports 80,443 used. You can technically use cloudflare tunnels, provided that you don't want custom domain support.

To start, SSH into your vps and create a new `docker-compose.yaml` file.

You should (for organizational purposes) put this into a subfolder, my usual sorting for this is `compose/app-name`, so in this case: `compose/pages-server`

We're going to put the following template into it:
```
services:
  pages-server:
    image: codeberg.org/codeberg/pages-server:next
    restart: always
    container_name: pages-server
    ports:
      - 80:80
      - 443:443
    environment:
      - PAGES_DOMAIN=example.com
      - RAW_DOMAIN=raw.example.com
      - GITEA_ROOT=https://forgejo.example.com
      - RAW_INFO_PAGE=https://docs.codeberg.org/codeberg-pages/
      - ACME_API=https://acme.mock.directory
      - ACME_ACCEPT_TERMS=true
      - ACME_EMAIL=noreply@example.email
      - ENABLE_HTTP_SERVER=false
      - LOG_LEVEL=trace
      - DNS_PROVIDER=cloudflare
      - CLOUDFLARE_DNS_API_TOKEN=
      - CLOUDFLARE_ZONE_API_TOKEN=
      - CLOUDFLARE_EMAIL=your.email@example.com

```

If you plan on setting up a reverse proxy for the server, change the ports used to something else. (such as 81/444)

Now, we can begin to setup our enviornment variables.

Next, you need to change `"PAGES_DOMAIN"` to the provider you want to use, alongside with `"RAW_DOMAIN"`. The raw domain provides the raw contents of files, so for example, if I had an html file at site.example.com, I could go to site.raw.example.com and see the contents, and yes, you can already get the raw content with your browser via viewing the source.

You can also mount the entire volume of the container if you'd like to edit files such as the templates for error pages, however I chose to just mount what I needed, which is beyond the scope of this tutorial.

After changing our domains, setup your DNS provider. I'm using cloudflare, so I have to go into my profile settings, and create a new API token with the DNS Zone permissions for the domain I'm using.

__If the host you are setting this server up on has a static IP address, I recommend setting the "trusted IPs" for your api token to it's IP address to prevent potential misuse.__

We can then copy the API key (which isn't shown again!) into the `"CLOUDFLARE_DNS_API_TOKEN"` and `"CLOUDFLARE_ZONE_API_TOKEN"`

> ⚠️ I highly recommend that you use a .env file instead of putting your variables straight into the docker-compose file.
>
> As a reminder, this guide simply goes over getting the server up and running as quickly as possible. I will edit it in the future with a guide for the .env

Then, add your cloudflare account's email into the other variable. 

After that, we are indeed ready to start the server.

# Please make sure to properly forward ports 443 & 80 before we continue.

Run the command `docker compose up`, which will allow us to see the logs of the server. **DO NOT DO THIS YET UNLESS YOU DO NOT WANT TO DO THE FOLLOWING OR THE FOLLOWING DO NOT APPLY**


# Adding support for private repositories/forgejo instances that require signin to view.

If needed, we can setup support for login-walled or private repositories. If you are like me and have your forgejo instance set to require sign in, we need to go generate an API token as our admin account.

Go to your forgejo instance, and go to your account settings (Not the admin menu)

![Applications](/images/how_to_setup_codeberg_pages/applications.png)

Next, name your token, and click on the dropdown for permissions.

![Name Your Token!!](/images/how_to_setup_codeberg_pages/notyet.png)

Then, enable the following permissions. To my knowledge these are the only ones required.

![Required permissions](/images/how_to_setup_codeberg_pages/permissions.png)

Now, click "Generate" and copy the token it gives you. Paste this into the GITEA_API_TOKEN field.

If I told you to NOT start the compose stack just yet because you wanted to do this, now you can start it.

# Setting up a test site

Make sure that your DNS provider has a wildcard dns record setup which points to your server (set the subdomain/whatever to "*", might not be supported by some DNS providers.

Next, I'm going to create a new repository in my forgejo instance. It can be public/private, private only being supported if you setup your API token from earlier.

Name it "pages" and change the main branch's name from "main" to "pages". I'm only doing this for simplicity.

Create a new index.html file inside of the repository for testing, you can write whatever or even just put your website in now for whatever reason, however I chose to just put in a simple "Hello world!" into the file (yes, you don't need code you can just serve text in html if you want)

Now, assuming our server is running (docker compose up if you haven't already), we can now navigate to ourforgejousername.ourdomain

(replace ourforgejousername with your username on your forgejo instance, and ourdomain with your domain from earlier)

You may get an SSL warning if you didn't setup let's encrypt (we haven't done that yet), so that's fine, ignore it and continue.

You should now see your html file from earlier.

# Setting up SSL with Let's Encrypt

If you want SSL, to, you know, work, here's how we're gonna do it.

Start by changing "ACME_API" to the following `https://acme-v02.api.letsencrypt.org/directory`.
Change ACME_ACCEPT_TERMS to true if you haven't done that.
Provide an email that's not invalid (unless you want to, though I believe that breaks let's encrypt's terms)

If you have your DNS provider setup already too, then this should work right out of the box.

Take down your server using `docker compose down`

and now start it up again using `docker compose up`

We can now make sure that SSL is working (you might get a warning on your first request to the site, if you do, just continue and the next ones should work fine, assuming you changed to let's encrypt.)

Finally, take it down again, and re-run with the command `docker compose up -d` to make sure that we can do other things in the os while the server is running.

There you go, that's the most basic setup of the codeberg-pages server for you. You can obviously tinker more, this is very surface level, you can even skip the part about testing and just go straight for enabling let's encrypt on first startup (which is what I did).