+++
title = "How and Why I Moved Away From Notion/Trello"
date = "2025-07-25T21:40:36-07:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "by you know who"
authorTwitter = "" #do not include @
cover = ""
tags = ["selfhosting", "alternatives", "privacy"]
keywords = ["notion", "Trello", "productivity", "privacy", "gaining control of your data", "notion alternatives", "Trello alternatives", "monday.com alternatives", "kanban", "kanban boards", "productivity tips", "selfhosting", "big tech"]
description = "In the past few months, I finally made the jump away from popular productivity platforms such as Trello and Notion. How, and why? You may ask. The main reason is that I wanted control over my data, get out of the limitations provided by solutions such as Trello/Notion and to be more private. So, what do I use now?"
showFullContent = false
readingTime = true
hideComments = false
+++
In the past few months, I finally made the jump away from popular productivity platforms such as [Trello](https://trello.com) and [Notion](https://notion.com). How, and why? You may ask.

The main reason is that I wanted control over my data, get out of the limitations provided by solutions such as Trello/Notion and to be more private. So, what do I use now?

# Great Question

I’ve migrated everything over to a selfhosted instance of [Nextcloud](https://nextcloud.com). While it may not be the most polished, it’s overall quite good.

If you are wondering what nextcloud is, it’s a Open Source and selfhostable “content collaboration platform”, though for most people it’s a lot more like a fully selfhostable Google suite alternative (docs, drive, calendar, forms, etc). A lot of the good functionality comes from apps made by different people, though a lot of the good ones are straight from Nextcloud themselves.

>
> ![Nextcloud's App Store](/images/notion-trello/nextcloud-apps.png)
> *Nextcloud's App "Store"*


It’s allowed me to replace Google almost entirely in my work and day-to-day, from document editing with a [collabora](https://www.collaboraonline.com/) integration (I’ve been experimenting with [Proton Docs](https://proton.me/drive/docs) as well), to storing files, and of course the topic of this post, productivity.

I have my instance of Nextcloud fully selfhosted, with backups outside of my servers (obviously) to make sure I don't lose my data.

To replace Trello/Notion’s [Kanban boards](https://en.wikipedia.org/wiki/Kanban_board), I’m using the Nextcloud Deck app, which, although it has some jank on rare occasions, I find it quite nice.

![Deck Example](/images/notion-trello/deck.png)

Combined with a [mobile app](https://apps.apple.com/us/app/nextcloud-deck/id1570892788) made by someone (which is a little janky), I can very easily manage my tasks from anywhere, alongside integrate it all with other things on my instance, from scheduling, to attaching files, and more.

Deck also has a great amount of support for Collaboration, with support for user assignments (just like Trello and notion) and comments + an activity log for each “card” in the deck.

![Deck Example](/images/notion-trello/deck-descriptions.png)

The only potential issue with Deck is the performance at a large scale:

> Performance limitations
>
> Deck is not yet ready for intensive usage. A lot of database queries are generated when the number of boards, cards and attachments is high. For example, a user having access to 13 boards, with each board having on average 100 cards, and each card having on average 5 attachments, would generate 6500 database queries when doing the file related queries which would increase the page loading time significantly.
>
> Improvements on Nextcloud server and Deck itself will improve the situation.

Next up is [Notes](https://apps.nextcloud.com/apps/notes)/[Collectives](https://apps.nextcloud.com/apps/collectives). I’m bunching these together because I use them both almost as much.

[Notes](https://apps.nextcloud.com/apps/notes) is what you’d expect, it’s a basic markdown-formatted note-taking app. 

>
> ![Notes App](https://raw.githubusercontent.com/nextcloud/screenshots/master/apps/Notes/notes.png)
> *Nextcloud's Notes App. Would have used an example from my setup however I use it for a wide variety of things so as such here's the example image. Credit Nextcloud.*

[Collectives](https://apps.nextcloud.com/apps/collectives) are made to be a knowledge-base, and I treat them as such for myself.

A collective is basically this, when you create a collective, you have your main page, and can create as many other pages as you want.
Each page is also markdown-formatted, and there’s not much more to it.
(show example of one of my collectives, with stuff blurred/covered)

>
> ![Example of a Collective](https://raw.githubusercontent.com/nextcloud/collectives/main/docs/static/images/screenshot.png)
> *Example of a collective, would've used one of mine but I have a lot of stuff in there that I'm not quite yet ready to share or show. Credit Nextcloud.*

I’m still getting fully comfortable with everything, but being able to manage/edit/store/have everything (primarily for game dev) such as docs, notes, deck, scheduling, and more all in one place has been great and highly helpful for my overall productivity, and all of this, with nobody ever being able to see my data, as it’s all self-hosted on my own infrastructure.

I could go on and on about moving off of bigger platforms/ecosystems and services that don’t respect your privacy such as Google, and might do so in the future, but this is one of many steps you can take to gain control of your data.

While Notion doesn't sell your data, there's nothing stopping them from going into my/your notes/pages/boards and seeing everything that I do, same with Trello.
Trello on the other hand seems to sell/share some of your data (ip address, user agent, other identifiers, just not anything from your boards/cards) to their "advertising partners" to "to build a profile of your interests and show you relevant adverts on other sites.", However you can opt-out of targeted advertising through their cookie consent thingy, sending a DNT request via your browser (if it supports it), etc.

# Other reasons why I made the switch
For some backstory, One of Trello’s main standout features is it’s Kanban style boards, which is one of the main reasons why people use them. I have also taken a look at “alternatives” such as Monday.com, but never ended up using them.
I stopped using Trello at some point due to me finding Notion, and because Notion had a Kanban format available, I used Notion as an all-in-one for notes, tasks/organizing, and more. However, I had concerns about how my data was being handled on both.

Notion does have an AI, which got quite annoying very fast as it became quite intrusive being in every single corner of the application, from the bottom right of the screen, to on popups for selected text, to being the first option when you type ‘/’ for custom blocks.

The cool (and scary) thing about notion is that it seems that they want you to do basically everything through them. They have a calendar, mail, and of course everything else. Some of notion can be genuinely powerful but I never found myself doing any automation or complex stuff, which is one of the main reasons why I made the switch.

Notion is also quite limiting for teams, me and some friends had tried to use Notion to keep a project of ours organized and keep everyone on task/on track, and well, we hit limitations (block count) quite quickly. I feel that their pricing structure is likely targeted at buisnesses and larger companies, not the average small group of friends trying to use notion for a few things.

We’re now on Trello and trying to find a good solution for documents, as to my knowledge Atlassian’s Ecosystem (which includes Trello) doesn’t have anything that would work for us.


That’s all for now, if you enjoyed and want to see more check out some previous posts or subscribe to the RSS feed to get new posts right to you.

See you next time with something awesome,

- Driver

oh, and also, you won’t see this message here again after the next post, but I’ll be leaving a quote that I heard/read at the end of these posts. Here’s the one for today:

> “It is not so much what happens to you as how you think about what happens.” - Epictetus