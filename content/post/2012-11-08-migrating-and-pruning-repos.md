---
author: Douglas Drumond
featured_image: /assets/images/cover.jpg
categories: ""
date: "2012-11-08T00:00:00Z"
tags:
- git
title: Migrating and pruning repos
---

Recently I had to put a folder from my app repository into a separate
repository on its own. The easiest way was just `git init` a new
repo, copy the directory and `git commit` it, but I would lose
all history up until the move. After fiddling with git and [Stack
Overflow](http://www.stackoverflow.com/ "Stack Overflow"), I found the
solution.

Suppose the structure is like this:

    All-in-one repo:
    * server
        * code.go
        * code2.go
    * iOS
        * code.m
        * code.h
    * Android
        * src
            * com
                * cafelinear
                    * myapp
                        * Code.java
                        * Code2.java

We want to move the server code into its own repo, so, final result will
be like this:

    Mobile repo:
    * iOS
        * code.m
        * code.h
    * Android
        * src
            * com
                * cafelinear
                    * myapp
                        * Code.java
                        * Code2.java

    Server repo:
    * code.go
    * code2.go

First, clone the original repository to the new one (the one that will
keep just the desired folder) and `cd` into it:

{{< highlight bash >}}
git clone /path/to/full/repo.git server
cd server
{{< / highlight >}}

Since this will be a new repo, remove the remote:

{{< highlight bash >}}
git remote rm origin
{{< / highlight >}}

Remove any tags you don’t want. Mine had a pattern, all started with v
(such as v-0.0.1) for all mobile apps. Server code had different tags,
making it easier for me:

{{< highlight bash >}}
git tag | grep \^v | xargs git tag -d
{{< / highlight >}}

Now, the magic:

{{< highlight bash >}}
git filter-branch --tag-name-filter cat --prune-empty --subdirectory-filter server -- --all
{{< / highlight >}}

What?

`git filter-branch` is used to (guess what?) filter branches (clap
clap clap). It modifies revision history by rewriting the branches
in the last parameter, in this case `--all`. Since we passed
`subdirectory-filter`, it will consider this directory as the root of
the new repo (effectively removing all others). Some filters generate
empty commits, `--prune-empty` get rid of them. To update the tags to
point to equivalent commits (they're not exactly the same since some
parents are different, so changing sha1), use `--tag-name-filter cat`
(`--tag-name-filter` asks for a command, in this case, `cat`).

We got the DeLorean, travelled back in time and rewrote history, but
left a dirt directory for us. iOS and Android folders are still there,
although as untracked files, let's get rid of them with:

{{< highlight bash >}}
git add . #to let git be aware of them
git reset --hard #to tell them go away
{{< / highlight >}}

Delete old refs:

{{< highlight bash >}}
git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
{{< / highlight >}}

Now force git garbage collector to clean everything:

{{< highlight bash >}}
git reflog expire --expire=now --all
git gc --aggressive --prune=now
{{< / highlight >}}

Now add your new remote and push to it:

{{< highlight bash >}}
git remote add origin /path/to/new/remote
git push -u origin master
{{< / highlight >}}

