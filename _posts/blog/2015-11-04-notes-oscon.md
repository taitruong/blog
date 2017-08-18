---
layout: post
title: "The Business of Open Source"
categories: blog
excerpt: "Notes from OSCON Europe 2015"
tags: [oss, innersource, conferences]
author: hlgr360
share: true
date: 2015-11-04
---

Last week I had the chance to attend the OSCON Europe conference in Amsterdam. I would give the conference an overall good rating, but I was missing a bit the excitement and drumbeat (and some roadmap discussions) of leading Open Source foundations like Mozilla, Apache, or even Open Source companies like Docker. There was an interesting (photoshop'ed) teaser in the keynote on the second day by the energetic founders of [Phusion](http://www.phusion.nl) Team about 'The Business of Open Source'. I would have loved to hear more about it - but maybe it was a clever marketing ploy to see if attendants would actually go out and ask the O'Really folks about that book. Well, it worked for me :)

The presentations were literally all over the map and the quality varied greatly. Some of the coding tutorials were interesting but lost me within the first 10 min by excessively scrolling back and forth and not providing the code snippets via Github. I was impressed by [Kubernetes](http://kubernetes.io) but asking me to create a Google Cloud account with a valid Creditcard as part of the workshop is a blatant attempt in developer trolling which I flat out refuse to follow. Both Google and CoreOS should have known better than trying to do that - and I am still surprised O'Reilly as conference organizer did let that happen. This is maybe appropriate at a sales event, but not at an Open Source conference (regardless if you are sponsor or not).

In general the first day was much stronger than the second one. But attending the 'Inner Soure' presentation from Paypal made the second day all worth it. Unfortunately there are no speaker slides  for this talk on the conference site, but you can read the gist of it in this [InfoQ](http://www.infoq.com/news/2015/10/innersource-at-paypal) article. I will certainly follow up on that one.

Ok, so lets get down to business and my notes. You can find speaker slides - if available - on the [OSCON](http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/proceedings) website.

#### Architecture as Code

* From the developer of tectribes.je (a tech community website)
* Adding the software developer as major stakeholder of software architecture
* Drawing pictures vs modeling system
* ‘Just enough software architecture’ -> there is a model / code gap
  * Already described in ‘Software Reflexion Models’ paper from 1995
* Only include architectural significant elements -> do not over specify for understanding
  * Analogue is to google maps -> street view vs directions
* Write architecture as code
  * Checkout [structurizr](http://structurizr.com)
    * Render architecture models from code
    * Architecture map(s) allows you to navigate from different level of abstraction down to source code
    * Java specification on Github
* If software architecture mode is in the code, it can be extracted from the code

#### Chaos Engineering (Netflix)

* Resilience is a feature
  * Embrace failure rather than avoiding it
    * Add fail-save patterns
    * Expect the unexpected for fall-back patterns
    * Cost of resilience is accuracy or latency
    * Tell upstream servers to use what you have
    * Use local storage in browser as last fallback
  * CAP theorem applies
    * Sacrifice availability or consistency, you can only have 2 out of 3
    * Best practices
      * Split out the control plane from workload
      * When you use a cloud provider like AWS, make a decision which part you use for either product or control plane
      * DNS and CDN are your best friends
  * Introducing failure to test resilience
    * Failure Friday (play chaos monkey manually)
    * You can not fix a single point of failure unless you know about it
    * Outages are unpredictable, failures can be introduced deterministically
  * Prevent propagation to avoid cascading failures
    * Use DNS: do geo routing with latency routing as fallback
    * Move traffic fast but not too fast to avoid overflow and cascading failure
    * Read the [Readwrite article on Netflix Chaos Engineering](http://readwrite.com/2014/09/17/netflix-chaos-engineering-for-everyone)

#### Pull Requests, not just for Code anymore

* Bad culture ruins good people
* Difference between implicit vs explicit culture
* You need to build explicit culture
  * Use github pages as repository for artifacts of culture
    * Engineering processes and policies
    * Architecture notes in RFC style
* Why is it different to a Wiki
  * You can only change a Wiki, but there is no review or approval
* Lessons learned
  * Learn git (offering classes and course)
  * Have a moderator to move things along and force closure
  * Be prepared for email flood (teach them how to use filters)
  * Encourage action: encourage pull request over encourage sugestions
  * With merge rights comes merges responsibility (do not leave them hanging)
  * Its not a democracy
  * Analogue to bonsai tree: a small team dedicated to growing and pruning it
  * Designate an entropy fighter (to delete outdated assets)
  * Embrace first day commit !!
  * Even the White House IT policy team is using it

#### Inner Open Source (Paypal)

* Moving from blocking/bottleneck to mentoring
* Scaling is a function of collaboration
  * Creating an environment which is self-healing and self-growing
* Build engagement through evangelism
  * 10% of team are trusted committers, not more
  * Focus on the positive of contribution, not necessarily if you agree with iit
  * All reviews are publicly documented
  * Require respectful and constructive communication
* Check out [Inner Source Commons](http://InnerSourceCommons.org)
