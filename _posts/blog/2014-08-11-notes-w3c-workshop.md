---
layout: post
title: "W3C Workshop 2014: The Web of Things"
categories: blog
excerpt: "Notes from the W3C Workshop 2014"
tags: [iot, conferences]
author: hlgr360
share: true
---

I had the opportunity to attend the W3C workshop on the Web Of Things in Berlin at the end of June. Here is a quick summary of my notes from the presentations and conversations - links to some the presentations can be found [here](http://www.w3.org/2014/02/wot/agenda.html) and [here](http://www.w3.org/2014/02/wot/report.html)

#### Siemens Smart Grid

* Uses XMPP as underlying communication protocol
* What does WoT and Chat have in common
  * distributed collaboration
  * from automation to collaboration
  * Spanning multiple domains requires extensibility
* Evolution
  * Webservices = workflows
  * Real-time Web = social web
  * WoT maps more closely to social web than workflows

#### Long Lived Connected Thing using EXI (binary XML)

* Large number of connected device -> large waste
* In general WoT devices will not follow smart phone lifecycle, but have to last 5 to 10 years
  * EXI allows the efficient use of XML for extensible message formats
  * Support full XML Schema
  * Uses XML Schema as grammar for efficient binary coding

#### Client-side energy demand management using Echonet Lite

* Utillity <-> Smart Meter <- Echonet Lite -> Home Appliances (client side energy consumers)
* Japan: Uses Echonet Lite as protocol for smart home energy management
* [Echonet Lite](http://www.echonet.gr.jp/english/spec/index.htm) ([presentation](http://www.w3.org/2013/07/mmi/slides/Umejima.pdf))
  * UDP based
  * 80+ device data models already defined
  * Traction outside of Japan in larger APAC as well

#### IoT Interop using web technologies

* Main Challenges and Recommendation
  * Connecting devices securely: use TLS
  * Provenance of data source: use PKI
  * Who has access to the data: use XACML
  * Endpoint Addressing: use endpoint URI
    * Consider intermittent connectivity
    * Consider endpoint might not be IP based
    * Discover endpoints: Feature URI (W3C standard)
      * (http://dev.w3.org/2009/dap/api-perms/)
      * (http://dev.webinos.org/specifications/api/)
    * Discover capability: [WebIDL](http://www.w3.org/TR/WebIDL/)
  * Local processing: Javascript
  * Remote invocation: JSON RPC
* Advanced
  * Local addressing: URI + PKI
  * Global protection: Policy sync across different endpoints

#### Android Web API server (Sony)

* Uses [WAMP protocol](http://wamp.ws)
  * Defined as subprotocol over websockets (but web sockets are not required)
  * Combines both RPC style and PubSub semantics in one protocol
* Neat concept of a Polling Manager
  * Enables passive sensors to become publishers
  * Polls passive sensors and publishes data on their behalf

#### Device Ensemble (Intel)

* Everything is a resource: sensor, capabilities, services
* Discovery, Authorization (UMA), Remote Worker
* Remote Worker
  * Offload compute heavy processing to cloud
  * Inspired by [HTML5 Web Worker](http://www.w3schools.com/html/html5_webworkers.asp)
* Device Addressing: [mDNS](http://en.wikipedia.org/wiki/Multicast_DNS), [NDS](http://www.novell.com/documentation/nds73/pdfdoc/10412671.pdf)

#### NodeRED (IBM)

* NodeRED is javascript integration IDE on top of node.js
* Allows for codefree integration flow design by graphically snapping together components
* Consists of IDE and runtime
* Allows use of javascript to act on or transform data in flows

#### Smart Social Spaces

* Filtering of data for quality and/or quantity
* WoT resembles more the graph structure of a Social Network

#### Authentication for WoT (Siemens)

* Example Connected Car
  * Separation of (security) concerns in car manufacture backend architecture
  * WebAPI Server + Car Backend Server
  * Client App calls WebAPI in backend, not car itself
  * Car Backend server communicates with car
  * Sensitive data, keys, etc of car are not accessible from WebAPI server but are restricted to Car Backend server

In particular I was intrigued by the [WAMP Protocol](http://wamp.ws) which I had not heard before. I subsequently contacted Tobias Eberstein from [Tavendo](http://tavendo.com) who is one of the key maintainers of WAMP. I will cover my conversation with him about some of WAMP's unique concepts in a follow-on blog post.
