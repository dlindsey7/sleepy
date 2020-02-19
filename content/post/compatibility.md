---
title: Compatibility and Regrets
description: Discussion about compatibility trade-offs
date: "2020-02-18T20:43:00+02:00"
publishDate: ""
---

Supporting old technology isn't always terrible.

<!--more-->

Today I realized I can't play half the Steam games in my library because I upgraded to MacOS Catalina. How I didn't notice this would be an issue is beyond me. Maybe I was blinded by my own work making products play nice even when they have no business doing so. Maybe the upgrade message got so annoying I caved without thinking. Maybe I just hadn't realized how many games I own. 

I get it though. Lines in the sand have to be drawn. No product can support everything all the time. New technology creates options that might be better in the long run but require sacrificing some existing features. At some point just about every workplace I've ever been at has said, "Let's make a bridge between the two. A compatibility mode." This is not the worst idea that will come up in a meeting but, in almost every instance, it's pretty damn close.

The worst project of this kind I ever worked on was an API that just could not satisfy every permutation needed to make the amazing new engine spit out the same results as the old one. In this case the new engine was built with improved hardware, dynamic rendering, faster processing, blah blah blah. The literal math involved was so different that this "bridge" API sucked up time, money, and brain power that would have been put to better use elsewhere. No one knew that going into the endeavor. The lessons learned allowed everyone to collectively decide that the new API would never act exactly like the old one. However, should a client need the old functionality it might be available depending on what exactly they needed. Not the best solution ever, no warm fuzzes, yet still valuable to someone.

The best version of compatibilty, if I'm being generous, is a project I'm currently working on. I can't go into too much detail. The important thing is that never ever in my life did I think an AJAX error function would be so problematic. It's like the bees in Candyman. You think those bees pouring out of his mouth are clearly the main issue to be dealt with and then surprise! He's got a knife.

Those two compatibility extremes got me thinking about another issue I've discussed with clients in the past. The SCORM profile for xAPI. I will be the first one to admit that I am shocked this idea works as well as it does. [Dual tracking](http://adlnet.github.io/xAPI-SCORM-Profile/dev/dual-track.html) to an LMS and an LRS is an interesting idea that would be helpful for clients that have both SCORM and xAPI courses. There is definitely a "move from LMS to LRS" application here. Long term I hope no company is insisting their tech team support storing student information in two seperate locations. That is biggest strike against trying to be both SCORM and xAPI. Another point is that you lose the broad profile scope available in xAPI by adhering to SCORM limitations. Of course in a situation where moving to an LRS makes sense the SCORM profile is a non-issue. Future courses would simply be created with an agreed upon xAPI profile that hopefully isn't too tied to SCORM. 

Changing technology guarantees features, products, browsers, what have you, will wind up being incompatible at some point. I know that's a vague way to put it but it honestly is that broad. Compatibility within programming is just a microcosm of adaptation in general. Given enough coffee I could go on about this forever. Especially since I have a lot more free time now that I can't play Planet Coaster, Party Hard, Lume... etc. 