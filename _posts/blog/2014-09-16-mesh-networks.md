---
layout: post
title: "Is IoT better described as Internet of Nodes?"
categories: blog
excerpt: "Are mesh networks the right answer for the Internet of Things?"
tags: [iot, blockchain, p2p]
author: hlgr360
share: true
date: 2014-09-16
---

The recent Gigagom article about [FireChat](http://semanticweb.com/open-gardens-firechat-adds-iot_b44343) caught my interest. In particular the following paragraph

```text
Open Garden’s apps all have one thing in common: they create networks on the fly from the connections all around us. These kind of ad hoc networks will connect nearby smartphones and tablets, each of which will act as node that can either receive data or pass it along."
```

Since peer-to-peer networks have been on my radar ever since a conversation with a "Hacktevist" at last year's [ThingMonk](http://thingmonk.com) I tried to dig a bit deeper into the underlying technologies. According to this [article](https://gigaom.com/2014/03/20/open-garden-retools-its-crowdsourced-mesh-technology-for-an-ios-messaging-app/) OpenGarden leverages Apple's [Multipeer Connectivity Framework](http://nshipster.com/multipeer-connectivity/) first introduced in iOS7 together with its very own [Multihop Connection](https://opengarden.com/Multi-hop_Wi-Fi_Offload.pdf) technology.

Why am I finding this intriguing? Well, first and for most because it provides a very viable example of the so called 'Sharing Economy' in a yet completely unexpected corner. Second, because IoT - for me at least - has so much more in common with a decentralized Social Network than with a Hub and Spoke (Cloud) model currently favored by the industry. Also the term Web of Things (WoT) better captures that notion than Internet of Things (See also my [Notes on the W3C Workshop on the Web of Things](https://hlgr360.github.io/blog/blog/notes-w3c-workshop/) I do need to clarify though that by Social Network I do not mean the centralized Facebook or Google+ data sinkholes, but rather the graph relationship between people (FOAF). Overlay that with the relationship of things to people and you have a magnitude more complex graph (FOAT - Friend of a Thing). Now combine the concept of a graph relationship  with a notion of interlocking network of domains ([or nodes as Michael Holdmann called it](http://mholdmann.wordpress.com/2013/05/11/iot-is-better-discribed-as-the-internet-of-nodes/)) and you see an alternative topology emerging, where things just talk within enclosed domains (things I carry only talk to other things I carry, or things in my house only talk to other things in my house, etc) without the need of a central server in the cloud or anywhere else (the afore mentioned Hub and Spoke topology).

In a previous Layer7 blog I explained the concept as follows

> **Where will the intelligence be in IoT? Will there be some form of on-site intelligence, so that core functionality continues even if the connection is lost? Or will all intelligence be cloud-based?** 
> It depends on whether you design for centralized “hub and spoke” or decentralized “domains of concern”. The former is responsible for correlating data and events within the domain whereas the latter is responsible for communicating with other domains (I owe this concept to [Michael Holdmann’s blog](http://mholdmann.wordpress.com/2013/05/11/iot-is-better-discribed-as-the-internet-of-nodes/)). “Domains of concern” design communicates with different domains for different purposes –  in an apartment for home automation, in an apartment building for HVAC, in a city block for energy generation/consumption, in a city for utility grid etc. Emergencies or out-of-bound signals are handled like exceptions and are bubbling up through the domains until intercepted. But most things will serve an inherent purpose and that purpose will not be affected by the absence of any connectivity. There will be intelligence within the core of each domain as well as at the edges/intersections with other domains.

I find that idea so much more attractive because it completely invalidates the notion that somehow we have to surrender our data to some central server in the cloud to get the benefits of IoT. The fact is - as soon as your data in on someone else's server in the cloud, you have to trust that this data is not being mined and resold to the highest bidder. Based on what I have seen so far too many startups jump on the bandwagon of easy money and base their business model on 'selling data about their user' rather than 'selling value to the user'.

My interest in Mesh and Peer-to-Peer Networks is based on the dislike of having someone offer me a marginal value-added service as the carrot to collect and mine my data and sell it for big bucks (having spent the first 20 years of my live under a communist surveillance state makes me a big fan of individual freedom and right to privacy). I was planning to look more into how some of the early music sharing services had used peer-to-peer networks like [BIttorrent](http://www.bittorrent.com) to archive global scale while explicitly designed to avoid central servers. And obviously I was not alone thinking alongs those lines, as recent work by IBM Research into [combining Bitcoins block chain encryption with Bittorrent](https://gigaom.com/2014/09/09/check-out-ibms-proposal-for-an-internet-of-things-architecture-using-bitcoins-block-chain-tech/) shows.

By the way - I will be heading out [ThingMonk](http://thingmonk.com) in London again this year. Together with [ThingsCon](http://thingscon.com) in Berlin these two are the conferences to meet the most diverse and creative crowd on all things IoT .