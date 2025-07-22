+++
title = "First Post: My Experience with CrowdSec"
date = "2025-03-21T20:57:42-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "Itsyourdriver"
authorTwitter = "itsyourdriver_" #do not include @
cover = ""
tags = ["cybersecurity", "linux", "review", "opinion", "overview"]
keywords = ["crowdsec", "linux", "firewall", "security", "cybersecurity"]
description = ""
showFullContent = false
readingTime = true
hideComments = true
+++

## Update: I intend on writing a follow up to this post in the near future with more info and an overview of my current stup with scripts and other presets for you

I recently rebuilt my homelab setup, and with it, I decided to install [CrowdSec](https://crowdsec.net) on my machines. For the uninformed, Crowdsec is "a behavioral solution that detects and blocks malicious IPs based on their behavior. It offers a Security Engine, a Console, a Remediation Component, and an AppSec Component for infrastructure and application security."
It basically offers an advanced firewall (you'd want to keep UFW or whatever you're using), detections for different vulnerabilities, SSH Brute force, http probing, etc, and frequently updated ip blocklists.

I started by signing up, and then getting my servers registered in their console as "engines", and setup a remediation component. Specifically the firewall one, as I felt it would be fine for my usecase. The first thing that I noticed was that on the free tier, you are limited to just three **free** blocklists per account, without a [paid subscription](https://www.crowdsec.net/pricing#saas-enterprise). Not a huge deal, I can understand the majority of paid plans, althoughs some people may believe that $31 per "security engine" each month is a little absurd for most people, however you have to consider that this is for companies, not individuals. (this is the enterprise plan)

![CrowdSec's paid plan](/images/my_experience_with_crowdsec/enterprise.png)


The three blocklist limit does suck, however you can always use a different application/firewall to block ips on lists from places such as [blocklist.de](https://www.blocklist.de/en/index.html), [FireHOL](https://iplists.firehol.org/), [IpThreat](https://ipthreat.net/lists), [or even these lists that I stumbled across](https://github.com/Aetherinox/csf-firewall).

I'm not going to get into the ways to do that here, as this focuses on CrowdSec specifically.
Up to this point, I hadn't gotten any alerts, it was all quiet. This is a good thing (assuming I set it up correctly), however the real fun with CrowdSec came after I installed & set it up on a VPS that I have.

As of now it's gotten 249 alerts, and the day that I put it on I swapped out [Fail2Ban](https://github.com/fail2ban/fail2ban) with CrowdSec, as CrowdSec prevents SSH bruteforce. If I need it to monitor logs for my applications, then it will be coming back for sure, but I was only using it for SSH login attempts.

It also happens to do a lot more than just SSH Bruteforce, it also blocks requests attempting to abuse different vulnerabilities. (not a huge issue if your servers are patched up, but it is nice to have)

## On the topic of SSH Bruteforcing, should you swap this with Fail2Ban?

*It depends.* If you use Fail2ban for more than just SSH, then keep it, you can add CrowdSec to stand in for the SSH protection that Fail2Ban comes with.

![Silly Alerts](/images/my_experience_with_crowdsec/list.png)

This is quite nice. the VPS it's running on is quite small in terms of the resources it has, and as such it needs all the help it can get.

CrowdSec supports many other Remediation Components/Bouncers (basically what actually blocks traffic) besides just at the firewall level.

![The List](/images/my_experience_with_crowdsec/components.png)
*(There are also many other bouncers available for other applications, services, and proxies)*

The way each component works is different, on their documentation they say:

> - nginx will check requester IP against the local API before granting or denying access.
> - firewall will add IPs to nftables/ipset set.
> - cloudflare will add IPs to the Cloudflare firewall.
> - blocklist will serve the blocklist to a appliance such as pfsense, fortinet, untangle via a http server.


In Conclusion, what is my overall opinion on CrowdSec?

It's decent. I do think that it is a decent service, especially so for enterprise customers (if all of their claims are true). If you just want it for blocklists (on the free tier) though, you'd be better off with lists sourced elsewhere as they will have more IPs listed.

Other than that, it works. I'd recommend it if you feel after reading everything it does that it would be worth it for you, especially if you don't have much else. 

If I got anything wrong here, please feel free to reach out.