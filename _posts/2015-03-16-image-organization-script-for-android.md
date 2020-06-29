---
layout: post
title: "Androidify.rb assets organizer"
date: "2015-03-16"
categories: "Open Source"
tags: ["Open Source"]
author: "Douglas Drumond"
background: /assets/images/cover.jpg
---

I just released [Androidify](https://github.com/douglasdrumond/androidify),
a script to move assets from iOS style naming to Android drawable folders.

Sometimes I do some UI work on [Sketch](http://bohemiancoding.com/sketch/) or
interact with designers who work with this tool. When it exports assets, it
uses the iOS naming convention of adding @2x or @3x to the file name. It’s
possible to add intermediate resolutions for export, and it creates a file with
@1.5x in name, and, for higher resolutions, it uses @4x. These sizes correspond
to Android mdpi to xxxhdpi sizes. There should be some plugin to export
correctly for Android, but I was bored at home and decided to create a script
for that. 

One day, I was working at Movile and the designer hadn’t yet finished our
Android assets, but he had finished working on the iOS design. To avoid being
blocked I decided to use the iOS assets we already had (later it would be just
a copy over to fix it) that were close enough to our Android UI. I remembered
my script and used it. 

A colleague was in the same situation and I showed him my scripted. He used it,
I had to adjust some things (even in this small script there was a bug), it
worked and I forgot about it. Then someday I was in the Recharging Area (our
kitchen) when a designer thanked me for the script. She used it to simplify her
workflow. That was when I realized this should be useful for more people,
despite being extremely crude.

So, here it is, on [GitHub](https://github.com/douglasdrumond/androidify),
available to anyone.
