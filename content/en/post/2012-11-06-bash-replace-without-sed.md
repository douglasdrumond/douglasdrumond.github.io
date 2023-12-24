---
author: Douglas Drumond
featured_image: /assets/images/cover.jpg
categories: ""
date: "2012-11-06T00:00:00Z"
tags:
- bash
title: Replacing in bash without sed
---

Bash has built-in substitution. For simple tasks it’s easier than piping through sed:

{{< highlight bash >}}
text="hello world"
echo ${text/hello/ohayou}   # prints ohayou world
{{< / highlight >}}

Be aware that just the first word is changed:

{{< highlight bash >}}
text="hello world hello"
echo ${text/hello/ohayou}   # prints ohayou world hello
{{< / highlight >}}

To change all instances of a world, prepend the search pattern with another slash:

{{< highlight bash >}}
text="hello world hello"
echo ${text//hello/ohayou}   # prints ohayou world ohayou
{{< / highlight >}}

Notice there are two slashes before *hello*, one as the separator and one prepending it.

