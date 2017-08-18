---
layout: post
title: "Event Horizon - The Future of APIs in IoT (revisited)"
categories: blog
excerpt: "Designing APIs for the Internet of Things"
tags: [api, iot]
date: 2014-10-10
author: hlgr360
share: true
---

Unless you have been hiding under a rock over the last year, you will have come across articles on the Internet of Things and its countless siblings like the Internet of Everything, or Industrial Internet or Web of Things. Part of my job is to track those developments and look for trends in API design which will inform our future product design.

While there is a passionate debate about how similar or different IoT applications and products to our current approaches, I think on key difference everyone can agree to is the increasing use of asynchronous message exchange pattern, also known as publish and subscribe. Our physical world is asynchronous: "stuff just happens". Ofcourse this is nothing new in the enterprise world - IBM pioneered this pattern with WebSphere MQ and it is commonly used in financial institutions. And as it happens, interacting with the physical world is a lot closer to 'swiping a credit card' than the request response patterns examplified in HTTP. In fact the mobile industry has long been struggling to fit 'push notifications' on top of HTTP's request response protocol, using techniques like long poll to simulate true push notification while reducing the overhad of the mobile constantly polling the server.

Well, here is what I have learned regarding IoT protocols: It’s a zoo out there, with lots of protocols trying to become the next HTTP. And some candidates deploy a formidable array of marketing, making it exceedingly hard to cut through the marketing hype.

My current shortlist of main contenders is (in alphabetical order): CoAP
MQTT, XMPP. I might add STOMP to that list, just for its simple brilliance. STOMP is a text-based messaging protocol that has recently been extended to allow for binary content. Additionally, I’ve recently started talking with some transportation companies and learning about their use of DDS from OMG, which might be another candidate.

In the corner of residing champion, we have JSON/HTTP. Not content to see this protocol pushed into early retirement, advocates have been developing some very interesting approaches that attempt to ensure the continuing relevance of HTTP for asynchronous small messages – WebSockets and WebHooks being the most well-known. Hypercat, Simple Thing Protocol and EventedAPI represent just a small sample of the interesting approaches emerging to support async eventing and messaging with HTTP. A very interesting approach on top of Websockets is WAMP since it allows both RPC  and Pubsub style interactions.

Each protocol has weaknesses: MQTT and Coap appear to be weak in security; DDS seems to be complex to scale and has version dependencies; XMPP is considered heavy-weight. But they all have strengths too, of course: DDS has the deployments in the field to prove its relevance; XMPP supports EXI and WebSocket for efficiency and a proven track record for scalable networks; both DDS and XMPP are extremely mature and have built-in security. Given the industry interest in MQTT as well as Coap, I am sure that whatever security problems exist will be fixed as the usecases mature.

In addition there are other potential solutions emerging from the mobile app space which might impact this space. As we have build massively scalable distributed databases relying on a concept of "Eventual Consistency", mobile app developers are realizing that connectivity can not be taken for granted and are increasingly relying on a local data pesistence layer on the mobile device itself which is providing data synchronisation with the backend service. Most commonly such local data persistence layer is provided by mobile database clients from CouchDB and Firebase. Stongloop recently added a similar offline synchronisation support to its nodejs distribution. Data persistence through 'Eventual Connectivity' has the great advantage of providing consistent app behavior in both online and offline mode - and it takes only a small step to take the same technique to connected things and embedded devices.

Check out [my notes](https://hlgr360.github.io/blog/blog/notes-iotcon/) from the most recent IOTCon conference in Berlin - it has a wealth of techical details arond Coap and Mqtt. Some very interesting IoT usecases leveraging XMPP can be found in [my summary](https://hlgr360.github.io/blog/blog/notes-w3c-workshop/) of the W3C workshop on the Web of Things
