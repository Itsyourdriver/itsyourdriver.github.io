---
title: Services
url: /services/
layout: page
---

# Services

I host a couple of "alternative frontends" and (soon) other services which are completely free to use.

### Redlib is working again (9/10/15)
> Reddit has fixed their onion URL, so as such, my instance is back up and running.
> There is still an issue with the error "TOR connection failed", if you see this, reload the page and it should work. I think the issue is something to do with my setup, I'll mess with it soon. :D
>

> Check uptime [here](https://status.driver.fyi/). 
>
> **WARNING that the above status page is hosted by BetterStack which uses Google Analytics, nothing I can do about it for now until I replace it with something without tracking.**

- [LibreMDb](https://lmdb.driver.fyi) - A frontend for iMDb.
- [Quetre](https://quetre.driver.fyi) - A frontend for Quora.
- [AnonymousOverflow](https://ao.driver.fyi) - A frontend for StackOverflow and all of their sites.
- [Redlib](https://redlib.driver.fyi) - A frontend for reddit. Using a fork from [here](https://git.ptr.moe/baalajimaestro/redlib) to route traffic through reddit's onion service to prevent blocks (as my server is blocked by reddit due to their insane amounts of blocks on VPN/Datacenter IP addresses)


All are protected by [Anubis](https://anubis.techaro.lol/).

# Logging Info
Both my Reverse Proxy and Anubis take error logs.

The reverse proxy's error logs include info such as your IP address and user agent. While I'd like to disable these there is not currently a good way to due to what I am using.

I am working on migrating to something better, but it will take a few days.

These logs are not monitored, shared, or sold. I have no interest in what you are viewing. Error logs should not be common if ever happening at any point.


## What are alternative frontends?
I'll put it in my own words, Alternative Frontends are an alternative way to view certain websites (iMDb, Quora, etc) with no tracking, popups, or ads. They proxy your request for you (preventing data such as your [public IP address](https://en.wikipedia.org/wiki/Wikipedia:Get_my_IP_address), [User Agent](https://en.wikipedia.org/wiki/User-Agent_header), and [data used to track you across the web and link said data to your identity](https://en.wikipedia.org/wiki/Device_fingerprint)), and present the information from the website to you in a cleaner format.

In all cases, unless it is something that you run as an application and not use as a website, alternative frontends do NOT support using your account with said service (iMDb, Quora, etc).

You can find frontends for [all sorts of websites/services](https://github.com/digitalblossom/alternative-frontends).

If you want to automatically redirect from different websites to a frontend, check out a browser extension such as [LibRedirect](https://libredirect.github.io/).

(if the above extension isn't compatible with your browser (ex: you are using chrome), you might want to consider switching to something such as [Firefox](https://www.firefox.com/en-US/) or [LibreWolf](https://librewolf.net/).)

## Why won't you add these to the public instance lists of each frontend?
As of now, I don't know if my server can handle it. However, it's also because a few I use personally, and would rather not have them blocked. While I do take pre-emptive measures (such as using Anubis to prevent bots from scraping, etc), The only service that I see NOT getting blocked if there's more usage is Redlib, due to it being routed through Reddit's Onion Service. Otherwise, LibreMDb should be fine, since the official instance seems just fine despite my almost daily usage of it.

If my thoughts change on this, or I'm ready to start rotating IP addresses and have more preventative measures in place for everything, then I'll be adding them to the lists.

If you are reading this and happen to have created any of the projects that I am now hosting an instance of and have tips or a comment, please stop by my DMs/inbox on Discord, Email, or Matrix (@itsyourdriver_:matrix.org for now).

## Will you ever add any more services/frontends?
Maybe. As of now I wanted to do a host a few frontends that had either a lack of working instances or already had a bunch of working ones but that I used myself.

If I add anything, it won't be going on the same server for sure, expect the following in the future potentially:
- Rimgo (Imgur frontend)
- Scribe (Medium Frontend, would like an image proxy for this but I guess I'll try and do it myself)
- SearXNG (We are FOR SURE not going on the public instance list for this one, primarily because I can't easily keep the instance unblocked due to potential heavy usage)
- Mozhi (Translator frontend, think Google Translate, DeepL, Bing Translate, etc)
