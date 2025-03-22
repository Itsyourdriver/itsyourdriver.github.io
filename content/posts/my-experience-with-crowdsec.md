+++
title = "First Post: My Experience with Crowdsec"
date = "2025-03-21T20:57:42-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "Itsyourdriver"
authorTwitter = "itsyourdriver_" #do not include @
cover = ""
tags = ["cybersecurity", "linux"]
keywords = ["crowdsec", "linux", "firewall", "security", "cybersecurity"]
description = ""
showFullContent = false
readingTime = true
hideComments = true
+++

I recently rebuilt my homelab setup, and with it, I decided to install [CrowdSec](https://crowdsec.net) on my machines. For the uninformed, Crowdsec is a "a behavioral solution that detects and blocks malicious IPs based on their behavior. It offers a Security Engine, a Console, a Remediation Component, and an AppSec Component for infrastructure and application security."

I signed up, and started with the free tier. I got my servers registered in their console as "engines", and setup a remediation component. Specifically the firewall one, as I felt it would be fine for my usecase. The first thing that I noticed was that on the free tier, you are limited to just three **free** blocklists per account, without a [paid subscription](https://www.crowdsec.net/pricing#saas-enterprise). Not a huge deal, I can understand the majority of paid plans, althoughs some people may believe that $31 per "security engine" each month is a little absurd for most people, however you have to consider that this is for companies, not individuals. (this is the enterprise plan)

<div style="text-align: center;">

![CrowdSec's paid plan](/images/my_experience_with_crowdsec/enterprise.png)

</div>

The three blocklist limit does suck, however you can always use a different application/firewall to block ips on lists from places such as [blocklist.de](https://www.blocklist.de/en/index.html), [FireHOL](https://iplists.firehol.org/), [or IpThreat](https://ipthreat.net/lists).

I'm not going to get into the ways to do that here, as this focuses on CrowdSec specifically.
Up to this point, I hadn't gotten any alerts, it was all quiet. This is more than likely a good? thing, however the real fun with CrowdSec came after I installed & set it up on a VPS that I have.

As of now it's gotten 249 alerts, and the day that I put it on I swapped out [Fail2Ban](https://github.com/fail2ban/fail2ban) with CrowdSec, as CrowdSec prevents SSH bruteforce. If I need it to monitor logs for my applications, then it will be coming back for sure, but I was only using it for SSH login attempts.

I'm not sure if I'm the only one, but I find it quite satisfying seeing everything that's been blocked. It's also a little spooky but fun at the same time, kinda like seeing this one bot that keeps attempting to connect to something I have behind cloudflare about 3-5 times a minute, approx. every three minutes. It keeps getting served a managed challenge, and had done about 450+ requests in under a day.

Back on topic, It also happens to do a lot more than just SSH Bruteforce, it also blocks requests attempting to abuse different vulnerabilities (not a huge issue if your servers are patched up, but it is nice to have)

## On the topic of SSH Bruteforcing, should you swap this with Fail2Ban?

*It depends.* If you use Fail2ban for more than just SSH, then keep it, you can add CrowdSec to stand in for the SSH protection that Fail2Ban comes with.

![Silly Alerts](/images/my_experience_with_crowdsec/list.png)

This to me is quite nice, the VPS it's running on is quite small in terms of the resources it has, and as such it needs all the help it can get.

CrowdSec does use a noticeable bit of memory in the background if I can recall of the top of my head, but it's only signifigant if your machine/VPS doesn't have much RAM.

CrowdSec supports many other Remediation Components/Bouncers (basically what actually blocks traffic) besides just at the firewall level.

![The List](/images/my_experience_with_crowdsec/components.png)
*(There are also many other bouncers available for other applications, services, and proxies)*

The way each component works is different, on their documentation they say:

> - nginx will check requester IP against the local API before granting or denying access.
> - firewall will add IPs to nftables/ipset set.
> - cloudflare will add IPs to the Cloudflare firewall.
> - blocklist will serve the blocklist to a appliance such as pfsense, fortinet, untangle via a http server.

In Conclusion, what is my overall opinion on CrowdSec?

It's decent. I do think that it is a decent service, especially so for enterprise customers (if all of their claims are true)