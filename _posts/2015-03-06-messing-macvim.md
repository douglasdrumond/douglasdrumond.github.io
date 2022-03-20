---
layout: post
title: "Messing MacVim"
date: "2015-03-06"
category: "open-source"
tags: ["MacVim", "Open source"]
author: "Douglas Drumond"
background: /assets/images/cover.jpg
---

I published a new version of MacVim on last week Monday and was quite happy
with it. It was early morning, I published it at 7:30 AM (UTC-3) and went to
work. Of course, being an avid user of Vim, the first thing I did at work was
updating my copy of MacVim.

Then things went awry. MacVim crashed at launch (of course, it didn’t occur at
home). E-mails started popping on my inbox. Starting without a `.vimrc` was
fine, so it was a problem with plugins.  Probably I had compiled it against
wrong version of Ruby (I use RVM and install several Ruby versions, but MacVim
must be compiled against system Ruby), but I was quite sure I had issued a `rvm
use system` before. When I came back home, I tried to investigate a little
further and, as I suspected, it was Ruby (it crashed when I used Command-T
plugin). But how? Well, I was so tired that I went to bed and decided to look
at the issue later.

At Movile, my project is on a tight deadline, so, every time I got home, I was
so tired that I couldn’t focus. I tried, but postponed looking at the issue
(also, sometimes I tried but hit a dead end). Until, finally, last weekend
I decided to solve this matter. But first, my Mac was so slow and with a lot of
garbage installed that, instead of deleting each app and some files, I backed
up what was important and did something I was used to when I was a Windows
user: formatting the computer and reinstalling the OS. 

With a new OS, lots of disk space (even after installing some apps, I went from 10
 GB free to 80 GB), it was time to fix MacVim. I recompiled and ran it to
 collect logs and, guess what? It worked flawlessly, even with Command-T.
 I hadn’t installed RVM (still haven’t) and MacVim used system Ruby (some day
 earlier, I made sure I was compiling after `rvm use system`, but it didn’t
 work, it just got me some logs in Library/Logs/DiagnosticReports). I uploaded
 the build, marked as pre-release and went to work. MacVim worked flawlessly
 again, even on my work machine. People who complained about the bug sent me
 feedback telling that everything was fine now.

 So, even setting RVM to use system Ruby, MacVim was compiled against the wrong
 version of Ruby.

 Lesson learned: be careful and doubt everything. I sincerely apologize for
 being careless in my first release. I felt the pain as a user too, I upgraded
 and downgraded (as other users had to) because of my own carelessness.

 Another lesson learned: MacVim community is awesome.
