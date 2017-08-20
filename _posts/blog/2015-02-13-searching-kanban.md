---
layout: post
title: "My hunt for a good project management tool."
categories: blog
excerpt: "Finding the perfect open-source Kanban project management tool"
tags: [development, docker]
date: 2015-02-13
author: hlgr360
---

I am going to admit, Docker has me hooked. I had been dabbling with Chef and Puppet, but they always seem to be too powerful and too complex for my simple needs to quickly prototype something. With docker I finally have the ability to script my setups and (re)create them at will. Ofcoure there are gotchas - and I will write about them as I go along my merry ways.

Most of my public docker stuff can be found in my [docker-template](https://github.com/hlgr360/docker-templates) project on github.

The idea behind the docker-template repo has been to provide a simple way to evaluate some of the Open Source tools I am using or I would like to evaluate. I am certainly not going to start a rant why - in my opinion - open source is where user-led innovation is happening. Others have expressed that way more eloquently than I can. But what I can do is make it dead simple to run some of those tools I like and hopefully learn a thing or two in the process.

The last couple of days I was hunting for a good project management tool, Kanban style. I first came across http://taiga.io and the first two statements in their tag line "Free. Open Source. Powerful." caught my attention. Well, turns out that installing Taiga was far from easy and it became quickly messy with build errors left and right. I ultimately got a working image when stumbling over the [shutit](http://ianmiell.github.io/shutit/) project. Ian maintains an [impressive list of working Docker configurations](https://github.com/ianmiell/shutit/tree/master/library) for popular stacks - you should definitely check out if yours is listed. Unfortunately I ran into some breakage of using shutit's trunk, but Ian was incredible helpful and responsive getting it fixed and pointing me into the right direction (heck, he even pointed out a bug in my Docker file :)). After I got a local install of Taiga.io up and running I realized that the tool emphasize has been on 'Powerful'. It just did not do it for me - and it tried to do way more than I wanted.

So back to the drawing board (aka github search) and I came across [Kanboard](http://kanboard.net). First thing to notice is that he starts with an introduction of Kanban (which is more than just the board). But what really caught my attention was his second bullet: **Limit your work in progress to be more efficient**. You see, Kanban is a methodology to guide you towards single piece flow. While it should be immediate obvious that focussing on one thing will lead to faster execution, less waste, and higher quality, the reality is (obvious for everyone who has done Value Stream Mapping), most of our time is spend in context switching and being blocked and working on a multitude of things in parallel without proper focus on what the right thing is we should be doing from start to finish. Now multiply that by n if you are a team without visibility and you end up in the usual project management mess which delivers the wrong thing over budget with inferior quality and over time. Kanban proposes to start tackling this problem by limiting the number of tasks which can be 'in process' at any given point in time. Meaning if you want to start a new task, but you already have x tasks in process, you first need to finish one of the on-going tasks before moving the next one from 'planned' to 'in process'. Add to this that the Kanaban board is visible to everyone in the team and you can start pushing for an alignment across the project. And start having the real necessary discussions on 'The definition of done' and 'What is the right thing to do next'. (Just as a side note: for the latter I am intrigued by the [Cost of Delay](http://blackswanfarming.com/cost-of-delay/) metric.)

So Kanboard hit all the right buttons and seemed to have just enough functionality of what I wanted to have. Plus it was super easy to setup and to navigate. You can check it out by either using [my Vagrant file](https://github.com/hlgr360/docker-templates/tree/master/project) or build it yourself with [my Dockerfile](https://github.com/hlgr360/docker-templates/tree/master/project/kanboard).

If you like it, please consider to contribute such that we can have more 'really useful' software like this.

Happy hacking from my wintry mountain retreat in the Thuringia Mountains.