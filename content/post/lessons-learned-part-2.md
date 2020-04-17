---
title: Lessons Learned Part 2
description: A list of lessons learned recently
date: "2020-03-22T19:03:00+02:00"
publishDate: ""
---

A list of lessons learned recently.

<!--more-->

Here's a list of things I've learned recently:

* Using reflect in Go is really useful when dealing with black box issues caused by modules.
* Write descriptions in tickets (please past me, PLEASE).
* Some Hugo themes do not satisfy the CORS policy.
* Missing CORS policy is not an issue unless you type 127.0.0.1 rather than localhost.
* I tend to pick history links based on port and might not notice FOR HALF AN HOUR that I'm not using localhost.
* strings.TrimSpace(s) is wonderful but since it returns a slice, it won't alter the value inside an interface.