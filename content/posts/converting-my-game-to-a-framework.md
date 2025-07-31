+++
title = "Converting my Roblox game to a framework, stupid or insane?"
date = "2025-07-31T11:09:19-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "by driver"
authorTwitter = "" #do not include @
cover = ""
tags = ["gamedev", "roblox", "programming"]
keywords = ["quebec", "roblox", "frameworks roblox", "roblox framework", "roblox game framework", "quebec roblox framework"]
description = ""
showFullContent = false
readingTime = true
hideComments = false
+++
Over the past couple of days I have begun converting my Roblox game over to a framework, now the history of frameworks on Roblox is interesting, the most well known one to my knowledge being [Knit](https://github.com/Sleitnick/Knit), which is no longer maintained/is now archived and has some [issues outlined by it's creator](https://scribe.rip/@sleitnick/knit-its-history-and-how-to-build-it-better-3100da97b36).

Knit was based on a SSA (Single Script Architecture) system, which basically means that one script (think of a script as a file of code), controls / manages a lot of other scripts (specifically [ModuleScripts](https://create.roblox.com/docs/reference/engine/classes/ModuleScript)).

SSA isn’t bad, it can be a fine system to use for your game. There’s also MSA (Multi Script Architecture) as well, which I sorta had going excluding the part where everything was supposed to work together.

# So, why did I move over to a framework? And which one?
I moved because my game was built on 9+ month old spaghetti code. Now, not all of it was spaghettified, but a lot of it was, and the newer stuff, while cleaner, wasn’t integrated/connected very well due to nothing being organized properly or connected properly.

Here’s an example of my remote events folder, which contains events used to communicate from the server to the client and the client to the server. (my remote functions/bindable events weren't much better either)

Another thing to note, none of this is properly organized, likely 10-15 of these aren’t used or were used at one point but never properly removed for the fear of breaking something.

Do NOT be me.

> 
> ![My Remote Event situation](/images/converting-my-game-to-a-framework/remotes.png)
>

I’m now using the [Quebec](https://devforum.roblox.com/t/framework-quebec-typed-roblox-game-framework/3810890) framework, which some might say to me: “Why quebec? Are you crazy? The devforum post for it isn’t even a month old yet!”

You’re right, it is new. However, for me, Quebec just works. I find it easy to understand, and it was really the only framework that I could find atleast on the devforum that seemed to be actively maintained and didn’t have some sort of flaw with it.

I did take a look at other frameworks such as [Prvd ‘M Wrong](https://devforum.roblox.com/t/next-generation-roblox-framework-prvd-m-wrong/3136463) and [Artwork](https://devforum.roblox.com/t/artwork-the-framework-for-roblox/3775984).

Prvd ‘M Wrong seems to still be maintained (last commits/changes 3 weeks ago), alongside Artwork. However, after some testing, Quebec seemed to just work.
Now, it (to my knowledge) isn’t battle tested, same with the other two frameworks listed.

Quebec works off of the SSA system, but includes some really nice features such as Networking, Signals, and Channels.

# Quebec

Quebec has quite a few features, from Singletons (basically the services/things that you load), Lifecycle Events, Networking, Signals, Channels, and even Classes.

I won't go over everything here, but here's a quick (technical) rundown on some of the things listed above. If you have any questions, check out the [documentation](https://baxoplenty.gitbook.io/quebec-docs/) for Quebec.

Networking is what you’d expect, it’s a better (depending on who you ask) way to handle networking on roblox, as it handles a lot of the remote events / remote function stuff for you.

Signals are also what you’d expect, however in this case they are basically a wrapper for a BindableEvent.

I won’t go into explaining Channels, because I haven’t delved into them too much just yet.

Qeubec also handles a lot more. However I’m getting off track again.

I’m still converting my code over to Quebec, however doing so has made a lot of my systems much more integrated, and my networking a lot easier to manage, as I have the opportunity to redo all of that stuff.

I should have another update on how Quebec is going later into the year, as I should have a lot more done by then, as currently my time has been spent converting over.

The nice thing about Quebec is it’s relatively simple (alteast to me), meaning that if I wanted to move to another SSA framework or my own, it wouldn’t take me too long to do so.

There are quite a few upcoming (and potentially upcoming) features for Quebec outlined in the [Github Issues](https://github.com/BaxoPlenty/quebec/issues), which I’m excited for as some of them would speed up some systems quite a lot.


So yeah, there’s my update on how that’s going!
Thank you to BaxoPlenty for making (and maintaining) Quebec, alongside everyone else in this post.

have a good one, and keep on creating

- driver

and of course as I promised, here's the quote for this one. You will not see this reminder again. (as there will be a quote in every next post unless I forget.)

> "The flower doesn't try to attract bees. The flower blooms, and the bees come."  - Mark Nepo