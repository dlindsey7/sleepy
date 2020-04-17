---
title: I Am Root
description: How I fixed root when it suddenly stopped connecting.
date: "2020-04-16T09:37:55+02:00"
publishDate: ""
---

In a previous post I mentioned Sequel Pro was giving me a hard time. I hadn't yet realized how badly MySQL was broken.

<!--more-->
When I wrote [Lessons Learned Part 3](/post/lessons-learned-part-3/index.html) I incorrectly assumed that all my MySQL related problems were related to Sequel Pro. This isn't a new assumption for me. Sequel Pro has crashed so many times that even this unique error message barely registered as more than an annoyance. I also, incorrectly, figured that switching to MySQL Workbench would be the last step in setting up a database that had mysteriously disappeared. 

Okay, now I realize I never explained WHY I was running into database import errors. Unfortunetely there is no clear explanation. One day I opened Sequel Pro and all my local databases were gone. I hadn't done any major upgrades or changes recently. My best guess is Gremlins did it. By Gremlins I mean one of my two small children smashed on the keyboard in an attempt to get [Cosmic Kids Yoga](https://www.youtube.com/watch?v=T_0P5grVoyg) or Elmo to appear. At least, I hope that's what happened because I can (kind of) prevent that from happening in the future.

Back to the underlying MySQL problem. I setup a new schema using MySQL Workbench. Imported a copy of the database I needed. Everything looked beautiful. Sadly, my project couldn't connect to the database. The error message shown was `Error occurred instantiating store: this authentication plugin is not supported`. This error lead me to look into troubleshooting issues surrounding MySQL v8. 

Looking up MySQL v8 authentication errors for root, or really any user, lead to an enormous number of posts and articles about native authentication. An issue with my existing project expecting a form of authentication that was not being provided sounded plausible. So, I tried making root use native password authentication with `ALTER USER  'root'@'%' IDENTIFIED WITH 'mysql_native_password' BY '<password>';`. Sadly that resulted in this message, `ERROR 1396 (HY000): Operation ALTER USER failed for 'root'@'%'`.

At this point I was moments away from yelling at MySQL to let me do what I wanted to. I was root. As root I had certain privileges. Then I decided root was broken. The best thing to do was part ways and create a new user. 

I wasn't allowed to create a new user. Life sucked. MySQL had effectively shut me out. I went back to root to check what my privileges were. `SHOW GRANTS` for root, I was seeing this:
> `Grant usage on *.* to 'root'@'localhost'` 

Great! Root has all the privileges! Except that no, no it doesn't. MySQL v8 doesn't display privileges like that. According to the [documentation](https://dev.mysql.com/doc/refman/8.0/en/show-grants.html) `SHOW GRANTS` should explicitly list every single privilege root had. Which meant root had no privileges. Now that I knew root was missing all privileges I was able to investigate why that might happen. Finally, I had my answer. MySQL, installed with homebrew, was not installed correctly. [This stack overflow question](https://stackoverflow.com/questions/9695362/macosx-homebrew-mysql-root-password) finally provided a solution that worked for me. 

```
# After upgrading homebrew this worked for me
$ brew services stop mysql
$ pkill mysqld
$ rm -rf /usr/local/var/mysql/
$ brew postinstall mysql
$ brew services restart mysql
$ mysql -uroot"
```

A couple of notes. This solution only worked after I upgraded homebrew. It's also a very destuctive solution. Since my databases were already missing that destruction meant very little to me. I imagine that's not always the case. At least I hope that there isn't a huge number of Gremlins banging on keyboard related MySQL issues out there in the world.