---
layout: post
title: "Version Control Systems"
date: "2013-07-17"
categories: ""
tags: ["git"]
author: "Douglas Drumond"
background: /assets/images/cover.jpg
---

A while ago, Fábio Akita from [AkitaOnRails.com](http://www.akitaonrails.com)
launched the campaign “Beginners’s Friday” intended to help the new generation
of developers coming today. I’m totally buying into this idea and this is the
first post I’m doing in that direction with version control systems.

## Version Control Systems

What is a version control system? In the context of software development,
a version control, revision control or source control system is a software
designed to control changes to computer programs (as well as documents, sites
and virtually whatever you want). Gone are the days of copying and pasting
files and changing the name “index.php,” “index-2.php,” “index-now-works.php,”
“index-now-it-really-works.php” and so on. In fact, those days should have
never existed in the first place, since revision control systems are hanging
around for a really long time (well, they’re older than me, as we’ll see
below).

## Motivation for version control systems

In software development, requirement changes, code evolve, bugs are introduced,
bugs are solved, bugs come back (these are called regression bugs), ideas come
and go. Writing code is pretty much like writing texts. Sometimes it’s writing
an article, sometimes it’s writing a book, but, as in writing, we revise, clean
up, rewrite parts and change ideas. A lot. If code was written exactly how it
meant to be, requirements never changed and software never evolved after
publishing, source control wouldn’t be necessary. But what if you want to go
back to some older idea that now really makes sense? Or discover a bug and need
to find when it began? There’s an really easy-looking way to do this that
doesn’t require further software, but it’s cumbersome and really error prone
(and it’s not easy to manage after all, so it just looks easy). It’s the
_Copy, Paste, Rename_ method. You can copy the file, paste it elsewhere
and rename it to reflect the version somehow, maybe with an increasing number.
The other way is using a version control system, which does this automagically.

## Brief history of version control systems

Back in the Triassic age of computation, in 1972, a proprietary software called
[SCSS](https://en.wikipedia.org/wiki/Source_Code_Control_System) was developed
at Bell Labs for managing program source code and text files. Later, in the
Jurassic age of computation, 1982 (I was born in the Cretaceous age, 1983)
a software called [RCS](https://en.wikipedia.org/wiki/Revision_Control_System)
(for Revision Control System) came to life. I never used them, so I won’t talk
about them.

In 1990, CVS launched (in fact, CVS started as a bunch of shell scripts in
1986), but it had (and still have) some limitations that led to development of
Subversion, also known as SVN, in 2000, to replace it. Subversion is still in
wide use today.

Until 2005 Linus Torvalds used BitKeeper to track changes in Linux source code.
BitKeeper is a proprietary software, but they licensed it for free for using in
Linux kernel as long as kernel mantainers didn’t try to develop a competing
software or didn’t try to circumvent some restrictions. After a developer
trying to develop a way to deal with BitKeeper metadata in order to support
more operations, BitKeeper decided to not license it anymore, so an alternative
was necessary. Linus announced he’d be switching VCS software and started
development of Git. At same time, Matt Mackall started developing Mercurial. In
the end, Linux kernel migrated to Git, but a lot of other developers also use
Mercurial, both were well accepted by the community.

Both Git and Mercurial share a common characteristic that is different from
previous VCS: they’re decentralized, while the previous are centralized version
control systems. By centralization I mean there’s a central blessed server
which everybody must connect into to download the source files, upload their
modification and do other tasks such as listing the change history of a file.
Git and Mercurial, on the other hand, download all history together with the
source files and provide ways to work locally without connecting to the central
server. In fact, the concept of central server in Git and Mercurial is just
political, not technical. One can copy and upload to another developer as well,
they don’t need to synchronize through a server.

In later posts, I’ll clarify these concepts with examples. Using my own Git
workflow, I’ll dig into some details and explain how Git works.

