---
title: Future Proof
description: Planning ahead
date: "2020-08-10T09:37:55+02:00"
publishDate: ""
---

I wish this meant I was building a time machine out of a cardboard DeLorean powered by tapping into my subconcious. In actuality it means weighing out client v. server side changes.  

<!--more-->
 I'm currently working on a [side project](/portfolio/aerials-app-project/) that will take in aerial skill names and display them. That sounds so incredibly simple. I'm sure you've heard similar pitches. One sentence. Super concise. Maybe throw in a buzzword or two. Then comes the explanation. Suddenly you're looking at a ginormous amount of work. 

In my case I'm the one who came up with the project but the issue is a pretty complex language problem. Aerial terminology has a decent amount of overlap. It's similar to dialects or regional phrases. I'd like to create a mobile friendly site that allows users to search a word or phrase. The results will have descriptions that will (hopefully) facilitate communication. The descriptions and examples should help make it clear that say, a "standard climb" and a "basic climb" are the same thing. 

Which brings me to my query design decisions and planning for the future. Previously I grabbed the entire skill set. This is not great. What happens when there are hundreds of skills? How do I handle filters? How hard would it be to switch searching from the client side to the server side later on? In the future I'd love to be able to do the following:

* Filter by level
* Filter by tag(s)
* Add more versatile tags
* Search on incomplete names
* Include pagination

None of that will happen if I take the easy way out, call GET once, and utilize some search strings on their own. Currently I've started planning by moving the name check to the server side. There's a lot more to be done, including tests and metrics, to make sure that approach is working as intended. For now, having a proof of concept gives me somewhere to start. Hopefully by fleshing out a simple search first, I'll avoid having to do a major re-work in the near future. Which, other than having a scalable project, is the real goal here. 