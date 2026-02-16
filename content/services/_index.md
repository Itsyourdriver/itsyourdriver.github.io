---
title: Services
url: /services/
layout: page
---

# Update on services.

## All frontends will be shutdown in around a week (2/22/26). You should migrate and remove my instances from your redirectors.


Hosted in the US with Oracle. I plan to swap providers in the future, I do not have any ETA on this.


All are protected by [Anubis](https://anubis.techaro.lol/). Planning on replacing with go-away more than likely as it provides a js-free challenge option.

As of now I am not interested in hosting any more frontends, though I have some I'd like to host in the future ^_^

# Logging Info
Both my Reverse Proxy and Anubis take error logs.

The reverse proxy's error logs include info such as your IP address and user agent. While I'd like to disable these there is not currently a good way to due to what I am using.

I am working on migrating to something better, but it will take a few days.

These logs are not monitored, shared, or sold. I have no interest in what you are viewing. Error logs should not be common if ever happening at any point.


## What are alternative frontends?
I'll put it in my own words, Alternative Frontends are an alternative way to view certain websites (iMDb, Quora, etc) with no tracking, popups, or ads. They proxy your request for you (preventing data such as your [public IP address](https://en.wikipedia.org/wiki/Wikipedia:Get_my_IP_address), [User Agent](https://en.wikipedia.org/wiki/User-Agent_header), and [data used to track you across the web and link said data to your identity](https://en.wikipedia.org/wiki/Device_fingerprint)), and present the information from the website to you in a cleaner format.

In all cases, unless it is something that you run as an application and not use as a website, alternative frontends do NOT support using your account with said service (iMDb, Quora, etc). Some of them may support local accounts, such as the case of Invidious.

You can find frontends for [all sorts of websites/services](https://github.com/digitalblossom/alternative-frontends).

If you want to automatically redirect from different websites to a frontend, check out a browser extension such as [LibRedirect](https://libredirect.github.io/).

(if the above extension isn't compatible with your browser (ex: you are using chrome), you might want to consider switching to something such as [Firefox](https://www.firefox.com/en-US/) or [LibreWolf](https://librewolf.net/).)

Alternatively you can find a generic redirector extension instead which should work on other browsers, however I won't be providing examples or links for those as I do not use them.

## Why won't you add these to the public instance lists of each frontend?
As of now, I don't know if my server can handle it. However, it's also because a few I use personally, and would rather not have them blocked. While I do take pre-emptive measures (such as using Anubis to prevent bots from scraping, etc), The only service that I see NOT getting blocked if there's more usage is Redlib, due to it being routed through Reddit's Onion Service. Otherwise, LibreMDb should be fine, since the official instance seems just fine despite my almost daily usage of it.

If my thoughts change on this, or I'm ready to start rotating IP addresses and have more preventative measures in place for everything, then I'll be adding them to the lists.

If you are reading this and happen to have created any of the projects that I am now hosting an instance of and have tips or a comment, please stop by my DMs/inbox on Discord, Email, or Matrix (@itsyourdriver_:matrix.org for now).

The only frontend that I broke this rule for is Phantom, as I felt that my instance being on the list would be beneficial as Phantom is still relatively new.

## Will you ever add any more services/frontends?
As of now I won't be adding anything.

If I add anything, it won't be going on the same server for sure, expect the following in the future potentially:
- Rimgo (Imgur frontend)
- Scribe (Medium Frontend, would like an image proxy for this but I guess I'll try and do it myself)


I will not host the following due to hurdles in getting them operational or other reasons:
- Invidious (might in the future, but we're talking many years in the future)
- SearXNG
- Safetwitch
- Nitter
