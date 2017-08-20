---
layout: post
title: "My hunt for a link sharing site."
categories: blog
excerpt: "Build your own Docker-ized Reddit clone with telesc.pe"
tags: [development, docker]
date: 2015-02-18
author: hlgr360
---

Continuing on my quest to create my own communication stack using open source - here is my experience creating a Docker-ized version of the [Telescope community server](http://www.telesc.pe).

A little bit of background on why I would want to have a dedicated link sharing and commenting site. Our team at the [API Academy](http://www.apiacademy.co) is primarily using Slack for team communication. Not because it is the best, but because it is the most convenient. Our communication patterns seem to fall into two buckets: IRC style discussions (and yes, I will publish a post on how to build your own Slack clone using IRC next) and link sharing. While there are merits to do both in one there are drawbacks too. My personal problem in particular around link sharing is Slack's presentation of content as a linear (chat) stream.

While looking for an adequate solution I stumbled over Telescope. And I am freely going to admit I have been blown away by its high quality look and feel. Unfortunately getting it to install in Docker wasn't as straightforward as I had hoped. Telescope is a Meteor application on top of node.js. If you were to install it step-by-step (aka RUN by RUN command) you will end up very soon in installation hell. If you execute the installation steps manually in a docker image it will work just fine. But doing the exact same sequence in a Dockerfile would fail.

Without much ado, here is what I had run into [credits](https://groups.google.com/forum/#!topic/meteor-talk/_WFeZUZQCqY).

```text
# the root cause is two fold - node's fs won't work across partitions so this problem would probably go away with some
# of the techniques in those links if implemented by meteor. But this is only a problem because Docker creates a new
# "image" for each RUN command, and so each step is isolated from the others.
```

The solution is as simple as combining the 'sensitive' shell commands into a single command line (such that they are executed within the same Docker image layer).

```sh
RUN git clone https://github.com/TelescopeJS/Telescope.git /app/telescope && \
cd /app/telescope && \
meteor update
```

You can find the working [Docker file in my Docker Templates project'(https://github.com/hlgr360/docker-templates/tree/master/social/telecope). If you like Telescope please consider contributing back to the Telescope community.