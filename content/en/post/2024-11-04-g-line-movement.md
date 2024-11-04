---
title: "Line movement with `g`"
date: 2024-11-04T12:09:56-03:00
tags: ["vim", "neovim", "vi", "tips", "TIL"]
featured_image: /assets/article_images/2024-11-04-some-vim-tips/wq-tattoo.webp
description: ""
---

If you have a long line in Vim, Vim wraps that line visually at window length.
It's not a hard wrap, no newline character is inserted. Since it's only one
line, if you try moving up or down with `j` and `k`, you'll notice that the
cursor moves up or down the group of lines (visually) corresponding to one line
in the file. The same happens when you type `0` or `^` to go to the beginning
of the line and `$` to go to the end.

If you want to move one line up or down, or to the beginning or end, based on
what's being displayed, prefix the movement command with `g`. For example,
type `gj`, `g$`, `g0`.


_Photo by the author_

