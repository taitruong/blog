---
layout: post
title: "Blockchain and APIs"
categories: blog
excerpt: "Notes from APIconUK 2014"
tags: [api, blockchain, conferences]
author: hlgr360
share: true
date: 2014-10-20
---

I presented on the Future of APIs in the IoT at the APIcon UK Edition in London last month.

In particular the presentation on the use of Altcoins for API moneytization was fascinating. While I am not yet convinced that this is the perfect use case for block chains it opened my eyes to the bitcoin infrastructure and its possibilities. It made more excited about catching up with Mehdi from oauth.io who is currently touring the conference circuit with a proposal [to decentralize authentication using blockchains](http://nordicapis.com/sessions/decentralizing-identity-by-mixing-oauth-and-bitcoin-protocols/). He will be presenting at the Nordic API Platform summit this month and our [API Academy API360 summit](http://www.apiacademy.co/api360/) in London in November.

Here are my notes on some of the presentations:

#### Delightful API Design (Uri, CTO of Mulesoft)

* ultimate buzz for creative lazy developer is to build your work on top of someone else's work
* imperative for success of API
  * need for speed
  * developer rules
  * simplicity
  * agile dev
    * iterative changes vs the need for API to stay constant
* Get the core right - steps
  * (1) design, document, mockup + live console => work through use cases and iterate
  * (2) generate client factories and server frameworks
* API specification
  * perfect testing surface
  * easier lifecycle mgmt: allows concise versioning (breaking vs non-breaking)
  * consistency
  * key for API first development approach
    * tells API consumer what to expect
    * tells API implementer what to deliver
  * steps: plan, design and validate, lock-down, implement, deploy, operate, start over
* UI -> UX = API -> APX (API Experience)
* RAML
  * steering committee: SOA Software, Mulesoft, Paypal, API Science, Cisco, Intuit, Angular,js, Box
  * very neat feature is the ability to define 'traits'
    * ability to template query parroters, response codes, etc
    * i.e. pageable, searchable, etc
  * API Designer: left side editor, right side resulting API documentation
    * for designing the API
  * API Notebook: moving API Definition from Designer to Notebook
    * creating SDKs and API mockup from RAML design
    * used for validation of API use cases
      * => enables structured TDD for API design
    * publish and share with API developer for validation

#### Which API description to use (Laura, SOA Software)

* if you are an enterprise, you deal with 100's of services
* until now no good way to concisely describe REST Services
  * enterprises implement Webservices by default
* Comparison between Swagger,RAML, and Blueprint
  * Blueprint not used in enterprises
* Swagger: code first, document second (bottom-up)
* RAML: design first, code second (top-down)
* Recommendation:
  * Use RAML if API design with LOB and less technical stakeholder
  * Use Swagger if you want to document code
* Practical experience
  * swagger-node-express:
    * use swagger spec directly in the code
    * documentation in code, stays in sync with code, but results in code changes when documentation changes
  * separate design docs
    * (+) allows (NLS) i18n for product documentation
    * (+) allows changes in documentation without code changes
    * (-) can get out of sync with implementation
  * gen doc from code
    * (-) need to touch code to change documentation
  * doc in code
    * (+) stays in sync with code
    * (-) changes impact code
* Thoughts on API platforms
  * should support Webservice as well as APIs
  * no focus on system-to-system integration, but on consuming side

#### The future of API Moneytization (apinetwork.io)

* using APIcoins (based on bitcoins) to moneytize API access and incentivize use
* http://www.apinetwork.co
* APIcoins are build on top of Bitcoin ledger
  * leveraging security infrastructure of bit coin
  * uses a technique called 'coloring': adding additional metadata to ledger to make it distinct from Bitcoins
* Challenges:
  * Bitcoin bloat for transactions: current limit is 7 transactions per second
  * New project called Factum runs hash over last n transactions and secures those n transactions with one ledger entry
* APINetwork uses Safenet as storage backend
  * Safenet = incentivised bit torrent like network for distributed file storage
* Security
  * in order to attack bit coin you need to take over 51% of Bitcoin network
  * has built-in incentive for new compute nodes to be added to Bitcoin network
  * at this point and with current growth pace only major state actors have the pockets to finance attack on Bitcoin network
  * private actors make more money by adding nodes
* New approaches like 'prove the stake' reduce computational power
* APINetwork incentivizes adding new services through issue of APIcoins

#### Follow-up floor discussions:

* Using blockchain algorithm for notaries, public ledgers like land registry, contracts, etc
* But human interactions are not simply back and white: for instance one can avoid or mitigate bankruptcy by paying of half of the contract (partial transactions)

#### API Business Models for Open Data (opencagedata.com)

* sustainable and scalable bmodell for open data
* competition: any way a customer is addressing the problem
  * direct competition: 4 P's (Product, Price, Promotion, Place)
  * indirect competition: education, awareness
* ways to compete with a service on top of open data
  * adding to open data: 1 + 1 > 2
    * annotations
    * go niche
  * curating open data: 1 - 1 > 0
* transactional moneytization gives incentive to use less
* alternative: price of pinboard.io = # users * 0.001
  * incentive to sign up early to pay less

#### Hackathons Deliver (Braintree)

* Hackathon (learn, build, share) vs Battlehack (competition)
* http://hackerpledge.org
* no cheap prices, no cheap pizza, no cheap beer
* **communication is king**
* hackathon is NOT a recruiting event
* if you want to recruit, inspire them
* a hack is not an app: motivation is to play around and discover
* links
  * http://hackcodeofconduct.org
  * http://hackdaymanifesto.com
  * http://mlh.io (Major League Hacking)
* hackathon is part of marketing:
  * define 'What success means' before you setup the event
  * track and measure
  * be present at the event and talk to participants (with devs, not marketing or sales)
  * share knowledge and experience
