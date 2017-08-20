---
layout: post
title: "From zero to SaaS in 6 hours and 40 min"
categories: blog
excerpt: "My Personal Hack-a-thon"
tags: [development]
author: hlgr360
share: true
---

I love my work. But from my wife's perspective I am an addict. Maybe it has to do with the fact that I started programming at age 14, turning a Z80 based electronic typewriter into a PC. To this day I remember the Z80 machine code from porting CPM to this wonderful 8 MHz 4k machine:

```text
36 41 21 00 FC 76
ld A, 0x41h
ld HL, 0xfc00h
ld (HL), A
```

Needless to say, it has been struggle for her to accept that I live and breath code all the time. And that there is no better time to read exciting books like 'Getting started with OAuth2' during vacation time (even though she does put me on an Email diet).

But last week I finally had the chance to put my skills to good use for her. Gabby - my wife - is doing a PhD at the Goethe University Frankfurt and is working with the City of Munich to put together a mobility program for young families.  Over a glass of wine (or was it breakfast?) she explained to me her difficulties of coming up with the best way for hundreds of participants to record their mobility patterns over a couple of days. Turning hundreds of pages of travel diaries into usable statistics does indeed look daunting. 'I can help you with that' I said. 'How about an online platform where your participants can record their travel behavior via an app or a webpage? I bet I can put something together usable in a couple of hours if you give me a day on the weekend and take care of the kids'. Guess what  - she took me up on my offer and I got her approval to stage my own personal hackathon on a Sunday. (If you are not a father of (three - in my case) small kids, you do not understand what it means  to sit in my coffee shop on a Sunday and hack away. It was like the old days!! And yes, I do love my kids)

My motivation - besides putting my coding skills to good use for Gabby - was to find out if our 'launchd.io' Ruby-on-Rails SaaS framework could be repurposed for other applications. We had put in quite some effort to get it right and have it work transparently underneath our application code without requiring obvious hooks. I even considered turning it into its own Ruby Gem.

To make it even more fun (and get some material for a blog article) I decided to keep notes throughout this very special personal hack-a-thon. So if you saw me at Starbucks in Esslingen yesterday, here is what I did:

```text
11.30 - Arrive at Starbucks, order coffee, setting up, plug in, selecting my heavy metal mix to 'get in the flow'
11.42 - Start coding (listening to Rammstein)
12:05 - Basic app layout created, initial setup of Gemfile dependencies (listening to Manowar)
12:15 - Start creating database migrations: active_admin, device, mobility protocol
12:30 - Basic database structure completed, database created and migrated (back to Rammstain)
12:50 - Copied forward multi-tenant and enum support, simplified tenant scope
13:20 - Initial version of data model done
13:25 - Admin, user and mobility protocol fixtures added and working (listing to German Punk band Toten Hosen)
13:30 - Copied database and heroku rake tasks forward, refreshing database to pick up changes
13:31 - Initial commit to git
14:00 - First complete cycle of creating, migrating, and loading fixtures into database using a multi-tenanted scope, first refill of coffee, second commit to git (as usual forgot to add new files) ) (Why am I listening to Dire Straits? Skip. Back to Rammstein. Better!)
14:40 - Active admin interface is up, registering user model for managing user accounts, copying basic Bootstrap styling and jQuery plugins (first some Silbermond, then East-German Plattenbau Rap from Disziplin)
15:45 - Initial landing page is up, login and redirect does not yet work
15:46 - Darn, had to remove public/index.html, now the redirect to default route works (Switching to Trance)
16:45 - Login works, travel entry index page works, adding localization
16:50 - Starting to work on popup form for adding travel entries (switching to classic: 'Eberlin - Missa a 2 choiri')
17:55 - Discovering that error_field seems to be a Postgres feature and not supported by Sqlite (Drat!)
18:10 - Adding a new travel entries through popup form works
18:15 - Created new private repo on Bitbucket and pushed local repo up
```

At this point an user could go to the landing page, log in, see the list of his existing travel entries and create new ones. You might cry foul and say that this is not yet a fully functional platform. And yes - you are right, but I had to pick up my oldest son from a birthday party.

Here are the remaining steps until I handed the keys (aka login credentials) over to Gabby this morning:

```text
15 min - Adding edit popup form for existing entries
30 min - Transitioning from Sqlite3 to Postgres for Heroku deployment
30 min - Setting up and initial deployment to Heroku
```

That's it. I continue to be in awe of the power of today's webapp frameworks and ease of initial deployment to a PaaS like Heroku. And yes - we have run into problems with Heroku deploying launchd.io (and it is probably worth exploring them in a separate blog article), but you can't argue with the result of these 8 hours - a fully functional multi-tenant app which is accessible worldwide.

PS: After reading the blog Gabby commented that I mentioned to love my work and my kids (and then she paused expressively). So let it be known that I love my wife too!