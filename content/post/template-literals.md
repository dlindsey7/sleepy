---
title: Tagged Templates in Typescript
description: Getting started with personal-web
date: "2020-07-01T09:37:55+02:00"
publishDate: ""
---

Mapped tagged templates in Typescript. For when you need to pass the tag along. Sounding as if you're doing an improv warmup is an added bonus. 

<!--more-->
Recently I was tasked with finding a way to make customizable wording for notifications. The project I was working on was designed to have key configurable files the client could edit in order to change certain behaviors. The challenge with that project usually lies in making a default that works for my development environment that can easily change to a custom setting without adding a bunch of extra code. Whenever I can use existing JavaScript concepts I try to do so. No one wants to learn a cutesy trademarked way to configure a complex system.

I was pretty determined not to reinvent template literals from the start. The tricky parts for me were fully understanding Tag functions and how to store them within a map. I sifted through blog posts, questions, and tutorials until I stumbled upon [gql](https://www.npmjs.com/package/graphql-tag). The fact that this existed told me that what I wanted to do (use a tag separate from where it was initially declared) had to be possible. Would it be feasible in Typescript? Maybe? I mean, yes, otherwise I'd be writing a very different post. Okay, backstory out of the way, on to the important stuff.

First I created an interface with a string and a tag function. VSCode was immediately unhappy. The interface needed to know, explicitly, what the tag function was made of and what it would be returning. I had assumed I could have a key/value pair that was string/function but I was wrong. The value needed its own interface where the tag function was the key and the value was the string returned. Now VSCode was happy and I could move on the provide the actual template function. I copied the tag template function from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) because it was pretty much perfect for my needs. My only changes were adjusting types to make Typescript happy. This all went into a file that client's are allowed to edit and hopefully not break. Lots of faith, trust, and pixie dust went into this project.

{{<gist dlindsey7 ca3a6e0876b8384b687ce8587d4cf8af>}}

The otherside of this, the side inaccessible to clients, handles the interpolation by creating a closure for the tag function. The gist shows calling interpolate and the function. In the actual project the calls are scattered throughout various files. I purposely stated the types passed into the interpolate function to avoid clients breaking the code by changing the innards of a template.

{{<gist dlindsey7 c6741726b79e031ddd39b77225c7c15c>}}

That's it! This feels like a modern ES6 approach while having the added benefit of being ES5 compatible. My favorite thing about this approach is that additional tag functions can be added without breaking everything.