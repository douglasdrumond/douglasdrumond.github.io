---
layout: post
title: "Understanding Android Open Source Project"
date: "2014-02-27"
categories: ""
tags: [""]
author: "Douglas Drumond"
---

A while ago someone asked on
[Quora](http://www.quora.com/Android-OS/What-are-some-good-ways-to-understand-the-Android-Open-Source-Project-source-code)
about some good ways to understand the AOSP. Although I don’t work with Android
internals anymore, it was fun looking back into AOSP and finding some sources
(no pun intended). Here’s my answer (edited for this blog):

Obviously, first go to [AOSP site](http://source.android.com/) and follow the
instructions to download the source.

Although outdated, take a look at [Android Platform Developer’s
Guide](http://www.kandroid.org/online-pdk/guide/index.html) (it’s a copy of the
old PDK, removed from Android site now). You can also check the source for
older tags, such as gingerbread, probably under docs there are instructions on
how to build the documentation. But don’t blindly follow them. Sometimes I find
it easier starting from where things started instead of diving into what’s the
current state.

I highly recommend setting up ctags, AOSP is just too big for Eclipse and you
can’t build it anyway using Eclipse (or Android Studio or IntelliJ). &nbsp;Or
try [GLOBAL](https://www.gnu.org/software/global/globaldoc_toc.html).

Chrome has a nice
[extension](https://chrome.google.com/webstore/detail/android-sdk-search/hgcbffeicehlpmgmnhnkjbjoldkfhoin?utm_source=chrome-ntp-icon)
developed by Roman Nurik, it adds an “ad” keyword to the omnibox to search
Android documentation and, the interesting point to your situation, adds
a “view source” link in documentation pointing to the source of that class
(look at screenshots in [Android SDK
Search](https://chrome.google.com/webstore/detail/android-sdk-search/hgcbffeicehlpmgmnhnkjbjoldkfhoin?utm_source=chrome-ntp-icon)
extension to get an idea of what I’m talking about). This way you familiarize
yourself with Android source code while developing normal apps.

Look at some patches sent to [Gerrit Code
Review](https://android-review.googlesource.com/#/q/status:open,n,z). Also, try
to solve some bugs in the [Issue
Tracker](https://code.google.com/p/android/issues/list), it’s an easier way to
focus on one task and not get overwhelmed.

I also recommend this book: [Embedded Android](http://amzn.to/1fkVK23) and some
Marakana/New Training videos:

<iframe allowfullscreen="" frameborder="0" height="279" src="//www.youtube-nocookie.com/embed/MlxiQNijniQ?rel=0" width="496"></iframe>
  
<iframe allowfullscreen="" frameborder="0" height="279" src="//www.youtube-nocookie.com/embed/1_H4AlQaNa0?rel=0" width="496"></iframe>
  
<iframe allowfullscreen="" frameborder="0" height="279" src="//www.youtube-nocookie.com/embed/rFqELLB1Kk8?rel=0" width="496"></iframe>
  
<p>
Some videos of Karim Yaghmour (Embedded Android author):

<iframe width="496" height="279" src="//www.youtube-nocookie.com/embed/KLUXPxxJc5c?rel=0" frameborder="0" allowfullscreen></iframe>
  
<iframe width="496" height="279" src="//www.youtube-nocookie.com/embed/LimC0XpeT0k?rel=0" frameborder="0" allowfullscreen></iframe>
  
<p>
Also, although not exclusive to AOSP/low level stuff, understanding how IPC is
done on Android is fundamental to understand Android:

<iframe width="496" height="279" src="//www.youtube-nocookie.com/embed/Jgampt1DOak?rel=0" frameborder="0" allowfullscreen></iframe>
 
<p>
Last, but not least, take a look at Android Builders Summit videos:

[Android Builders Summit 2011 (download list)](http://free-electrons.com/blog/abs-2011-videos/)
  
[Android Builders Summit 2012 (download list)](http://free-electrons.com/blog/abs-2012-videos/)
  
[Android Builders Summit 2013 (youtube playlist)](https://www.youtube.com/playlist?list=PLbzoR-pLrL6qsy2zR0s0uag75nxpoKxsy)
  
I’d do a shameless plug and link to my own presentation on this topic, but it’s
in Portuguese and indeed doesn’t make much sense without someone presenting it.
