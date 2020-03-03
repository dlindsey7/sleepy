---
title: Go Mod Init
description: When it gives you weird errors on go mod init
date: "2020-03-02T00:00:00+00:00"
publishDate: ""
---

Go mod errors and import funtimes

<!--more-->

Originally Go projects had a strict $GOROOT and $GOPATH to follow. That's when the troubles began. Unfortunately these weren't the kind of troubles Aubrey Parker could solve. 

Setting up direnv was a pain. Keeping a large number of unrelated projects under a single go directory was worse. So when go modules were first introduced I thought, "change is hard but this can only get better". I was right, with a few exceptions for pain points along the way.

The biggest issues I've come across are... limited examples and outdated issues. While trying to solve an import failure error I was getting I learned that Go changes have become so subtle that sorting through exactly what went wrong can be difficult.

In my case I wanted to use an example app documented in 2019 to learn the stack for MongoDB, Go, and React. I've worked with each individually but never in combination with eachother. Two hours of Google searches later I figured out my unique combination of broken things. 

First, go mod init was in the wrong place. Totally my fault, mistake, oops. Second, I updated Go to 1.14. This wasn't the worst idea ever but it'll be important later. Third, there were relative paths in the example. Those are not a thing in Go practice anymore. Let's all move on to the new glorious era of... not that (GOPATH free!).

Back to the biggest issue I ran into. When I upgraded Go, GO111MODULE=auto kicked in. GO111MODULE, this thing I'd known was important to keep track of suddenly stopped a setting that I had to babysit. It also meant I couldn't get it to turn off in order to make relative paths work. While it's obviously a terrible solution it's one that kept popping up in searches. 

Finally I did have an issue where go build didn't pull in every dependency. That one was easy to fix with "go get". I might come back around to figure that one out if it ever gets obnoxious. Right now I get to have fun cleaning up the bits of test code I went around subjecting 'go mod init' to.
