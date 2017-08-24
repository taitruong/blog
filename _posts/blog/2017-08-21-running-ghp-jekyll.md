---
layout: post
title: "Taking back control of your content - Developer style"
excerpt: "How to run a fully featured Jekyll blog on Github using CI/CD"
categories: blog
tags: [development, content]
author: hlgr360
share: true
---

Back when I started as API Evangelist for the [Layer7 API Academy](http://apiacademy.co) blogging, presenting and speaking in public became part of my job description. And very quickly I realized that something was horribly broken with the way we manage content. Somehow there was a fundamental disconnect between the level of control and agility I had when writing code and writing content. Doing the latter alwasy seem to involve awkward manual review processes and word documents and formatting and endless emails back and forth with different versions and initials. 

Since my new role coincided with a friend and I launching [launchd.de](http://launchd.de) - our lean business development platform - we tried to pick better tooling for our private blogging. Enter [wordpress.org](http://wordpress.org). Compared to the corporate blogging this was already quite a step up in terms of control .. but formatting still was more Word like .. and - looking back - it still lacked the clarity of versioning and diffing and collaborative features I am used to when writing code. 

In parallel a big topic in the API community was (and still is) [developer focussed API documentation](http://documentation.apievangelist.com) with plenty of startups tackling the challenge to create good looking and functional documentation for humans. And the ever present challenge of keeping documentation in sync with the API it describes. This further sensitized me about how (tech) writers and developers can engage in close collabroation to create a single customer facing product, the API.

Fast forward a year or two and Layer7 was aqcuired by CA Technologies and my 'precious' content disappeared together with the Layer7 brand and blog. It just went poof up into the digital ether, leaving me scrambling to reconstruct it. Roughly at the same time I heard first folks mentioning a concept of **Docs-as-Code** at conferences like [OSCON](https://hlgr360.github.io/blog/blog/notes-oscon/). By that time I was CTO of the [Haufe.Group](http://www.haufegroup.com) - and had the means to do it differently. So I decided to host our [Developer Blog](http://work.haufegroup.io) on [Github](https://github.com/Haufe-Lexware/Haufe-Lexware.github.io), or rather more precisely [Github Pages](https://pages.github.com). And I did not stop there - I took the talk [Pull requests, not just for code anymore](https://media.ccc.de/v/froscon2015-1525-pull_requests_not_just_for_code_anymore) to heart and published our CTO Office policies in a private repo as well.

In the meantime more folks are starting to think about [Docs-as-Code](http://www.writethedocs.org/guide/docs-as-code/) and [Docs Like Code](http://www.docslikecode.com): the folks from [WriteTheDocs](http://www.writethedocs.org) and [Ann Gentle](https://justwriteclick.com) respectively. Anne recently published a book called [Docs Like Code](https://justwriteclick.com/books/docs-like-code/).

My gut tells me that there could be even a bigger story yet - why stop at docs, and not just simply apply this model for content in general? [HaufeGroup](https://www.haufe.com/en/vision/haufe-group) with its roots as publisher is still producing plenty of valuable content but it is being locked up in traditional, closed-source and proprietory CMS's. But those ideas are best told in a blog post over at our [Haufe.Group blog](http://work.haufegroup.io) site. 

(Update: I just published [Treating our Content as Code: What DevOps and CI/CD can teach us about content publishing.](http://work.haufegroup.io/content-as-code/))

So it is only consequent that I first try to liberate my own content from Wordpress and friends. It should be obvious by now that my new blog will live on Git(hub) and be served through Github Pages. So I could have simply copied the format from our developer blog and be done with it. But to make things more interesting, I decided to go for a fully featured Jekyll blog. Github pages only support very few Jekyll plugins - for a more sophisticated website one needs to run Jekyll outside of Github and only push the generated pages into Github Pages. 

I picked the [So Simple Theme](https://mademistakes.com/work/so-simple-jekyll-theme/) and now had to come up with a way to generate the website. Obviously I could have done it [manually](http://varunbpatil.github.io/2013/07/06/jekyll-build-fail/#.WZV5qK2B3re) but that feelt wrong. No, if we are serious about 'content-as-code' than we should hold ourselfs to the same standard for publishing content as we do on building code. If I check-in a new post, I expect the toolchain to pick up the change and rebuild the site and deploy it automatically. I wanted a CI/CD pipeline for publishing content. A few google queries later I had found what I was looking for: [Using Travis CI to build a Jekyll site](http://pauldambra.github.io/using-travis-to-build-jekyll.html). Combining the manual build script with [travis-ci](http://travis-ci.org) gave me a sweet solution to have my cake and eat it too, all within a single Github repo. You can find the final build script [here](https://github.com/hlgr360/blog/blob/master/build-site.sh).

<figure class="half">
	<img src="/blog/images/running-ghp-jekyll/travis-ci.png" alt="travis-ci">
	<img src="/blog/images/running-ghp-jekyll/travis-log.png" alt="travis-log">
	<figcaption>Travis-CI build screens.</figcaption>
</figure>

And kudos to the [travis-ci](http://travis-ci.org) team for building such an awesome service. A special nice touch was the ability to include the build badges in the README of [my blog repo](https://github.com/hlgr360/blog).

Having solved the technical challenges, all what was left was a lot of busy work to liberate my content from its various prisons and walled gardens. You are obviously reading this blog already on my new site - so go ahead and explore some of my blog posts, videos and articels. I personally find the [tag page](https://hlgr360.github.io/blog/tags/) the easiest way to navigate across my content.
