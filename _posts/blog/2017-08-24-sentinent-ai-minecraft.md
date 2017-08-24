---
layout: post
title: "Building SentinentAI mod for Minecraft"
excerpt: "Getting back into the game - quite literally"
categories: blog
tags: [development, minecraft, ai]
author: hlgr360
share: true
---

The background to this multi-layered story requires a bit of patience on part of the reader but I  hope it will be worth it. 

First layer and setting the scene: You see, it is summer in good old Europe and vacation time is upon us. A couple of years ago my wife and I decided to not longer postpone our dream vacations of long distance hiking across Germany and Europe until our retirement, but start doing it now - with 3 kids and a dog in tow. This summer we were planning on hiking across the Black Forest on an old pigrims path. Since it is only us and the kids, those hikes tend to be an extremly intense yet very rewarding time for us as a family. There is no distraction, no gadgets - just nature, the long and winding path, two parents and three kids and the distinct possibility of ice cream at the end of a long day. Needless to say we have settled into some routine, like the kids telling their stories to us: made up or real - it doesn't matter. It is a time of talking and bonding over having to hike through rain and heat, forest and field. 

<figure>
	<img src="/blog/images/sentinent-ai-minecraft/blackforest.jpg" alt="black-forest">
	<figcaption>Somewhere in the Black Forest.</figcaption>
</figure>


Second layer and describing my state of mind: Recently I got back into reading Science Fiction and one of the best new books I came across was [The Long Way to a Small, Angry Planet](https://www.amazon.com/Long-Small-Angry-Planet-Wayfarers/dp/0062444131) by [Becky Chamber](https://en.wikipedia.org/wiki/The_Long_Way_to_a_Small,_Angry_Planet). I got completely lost in the story and was delighted to find that she had recently published a sequel called [A Closed and Common Orbit](https://www.amazon.com/Closed-Common-Orbit-Wayfarers/dp/0062569406). In the second book one of the main characters is the Spaceship AI system from the first book which had gained conciousness and had by now been transfered into autonomous human shell. I followed it by reading [Ready Player One](https://www.amazon.com/Ready-Player-One-Ernest-Cline/dp/0307887448/) from [Ernest Cline](https://en.wikipedia.org/wiki/Ready_Player_One) describing a dystopian future where the only remaining place to go to is an immersive virtual reality game (it reminded me in the basic layout of the story on [Snowcrash](https://www.amazon.com/Snow-Crash-Neal-Stephenson-ebook/dp/B002RI9KAE) by Neal Stephenson).

<figure class="half">
	<img src="/blog/images/sentinent-ai-minecraft/A-long-way.png" alt="long-way">
	<img src="/blog/images/sentinent-ai-minecraft/A-closed-orbit.png" alt="common-orbit">
	<figcaption>The Wayfarer Series from Becky Chambers.</figcaption>
</figure>

Third layer is what my kids are obsessing at the moment: [Minecraft](http://minecraft.org) ... I got my oldest son the book [Minecraft Modding with Forge: A Family-Friendly Guide](https://www.amazon.com/Minecraft-Modding-Forge-Family-Friendly-Building/dp/1491918896) and ever since then I have been on the hook helping him programming [Minecraft Mods](https://github.com/alx365/minecraft_mods) in Java. And I - quite literally - got back into the game myself. And I have to admit that I am impressed by the creative freedom and extensibility of that game, lemding itself for so much more than just building blocks. From [Quantmechanics](http://qcraft.org/about/) to [space travel](https://micdoodle8.com/mods/galacticraft/) to [programmable computer](http://www.computercraft.info), the variety and creativity is just mindboggling. 

<figure>
	<img src="/blog/images/sentinent-ai-minecraft/qcraft.png" alt="qcraft">
	<figcaption>QCraft: Minecraft Rocks Quantum Rules.</figcaption>
</figure>

Forth layer is my current role as CTO of fairly large sized company, with all its benefits and challenges. One of the benefits of my role is that I can freely go to conferences and learn about the state of the art (i.e. neuronal networks, serverless, machine learning, blockchain, etc). One of the bigger frustrations of my role is that my job is heavy on management and strategy and relatively light on actually doing some of those things. For someone like me - who has been writing software since I was 12 - this is hard to accept. I have alwasy seen myself as being a very strong technical CTO but it is getting harder and harder to maintain.

<figure>
	<img src="/blog/images/sentinent-ai-minecraft/cto-survival-guide.png" alt="cto-survival">
	<figcaption>CTO Survival Guide, from rainforestqa.com.</figcaption>
</figure>

Ok, so lets mash those layers together and see if we can get this story wrapped up. As we were hiking across the blackforest, my daughter told me a recent dream of her having a friend in minecraft who she can talk to 'like Alexa'. And in my head a million and one lights lit up and suddenly had this vision of using Minecraft to explore some of those AI concepts and natural language interfaces. And because of Becky Chamber's books I knew exactly how this would look like. And I knew exactly with what I would start ... with one of the oldest natural language processing programs I remember from my days programming with my Dad called [Eliza](https://en.wikipedia.org/wiki/ELIZA). But I would not stop there but I would like to give it the voice of Alexa, maybe throw in some of the [Cognitive Services from Azure](https://azure.microsoft.com/en-us/services/cognitive-services/), and the recently released [Conversational AI from Google](https://conversationai.github.io)

I don't think I will go as far as [Project Malmo](https://github.com/Microsoft/malmo) from [Microsoft Research](https://www.microsoft.com/en-us/research/project/project-malmo/) - but not because of a lack of aspiration, but more realistically because of lack of time. 

I decided to call this sweet little project of mine [SentitentAIMod](https://github.com/hlgr360/SentinentAImod) and I sure hope that my kids - and especially my daughter - keep me honest and on track to actually stay with it for long enough to have learned some of those technologies. I did spend some time with my son, setting him up with his own [Github Repo](https://github.com/alx365/minecraft_mods) and fixing his mod build process. 

If you want to tack along for the journey, stay tuned and check out my blog or subscribe to the [SentinentAIMod](https://github.com/hlgr360/SentinentAImod) repo.

<figure>
	<img src="/blog/images/sentinent-ai-minecraft/npc.png" alt="npc">
	<figcaption>NPC Character, from minecraft.org.</figcaption>
</figure>
