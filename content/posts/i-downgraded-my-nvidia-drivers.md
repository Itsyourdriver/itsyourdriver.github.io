+++
title = "I Downgraded My Nvidia Drivers"
date = "2025-04-10T17:35:07-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "Itsyourdriver"
authorTwitter = "" #do not include @
cover = ""
tags = ["drivers", "software"]
keywords = ["nvidia drivers", "nvidia driver issues","nvidia"]
description = "So, I downgraded my nvidia drivers due to the current ongoing issues, and well...."
showFullContent = false
readingTime = true
hideComments = false
+++

This is going to be a short post from me, I just wanted to post about this because it was quite annoying.
As some of you may know, [NVIDIA happens to be going through a very rough time with their GPU drivers](https://www.youtube.com/watch?v=NTXoUsdSAnA), with it being compared to AMD's previous problems with theirs.

I finally had the time recently to hop on VR to do some simracing, and since I hadn't been on my rig / headset in a while, I had to update everything, no big deal right? Well, think again. I had updated my GPU drivers a few weeks ago to one of the 572.x versions, and everything seemed fine, although I had some issues with weird artifacts on text and UI elements in certain games (mainly ready or not, some browser tabs even). So, as I updated my VR headset (a quest 2)'s drivers, my displays flashed black, no big deal right? Maybe it's just doing something that it needs to do, right? I mean it hasn't done it before but it's been months since I updated. Well, no. After about 1-2 more times, it just stayed black. I immediately knew what the problem was, rebooted windows. Luckily, I was able to boot back without problem, and I immediately started by downloading a new version of DDU, and downloading the installer for the last "stable" nvidia driver 566.36.

I then booted into safe mode, DDU'd+rebooted, disconnected my internet entirely before doing so (could've done this before), and went into windows normally without drivers.

I then went to install driver version 566.36 via the installer I had downloaded for my graphics card, and well, I had accidentally downloaded the laptop drivers (I use an RTX 3050, I tried upgrading to an AMD Radeon RX 6750xt but I had some driver issues that I believe were conflicts with something else on my system, haven't bothered ever since I returned the card), so I went onto my laptop and got the right executable onto my pc via an OLD usb drive.

Installing went fine, and was actually much smoother than I expected, I did have to fix my monitor layout again (which is really annoying and take a good few minutes), but after that, I was back up and running, and everything that I did after was pretty much issue free. (aside from general steamvr/quest 2 issues which I've had for ages)

I then finally booted up Ready or Not again today, and noticed that the artifcting was gone, alongside the text artifacting.

So, TLDR: Downgrade if you can, if you need to play a newer game such as Monster Hunter: Wilds or use a 50 series card, hopefully they're able to fix their problems soon. ¯\_(ツ)_/¯