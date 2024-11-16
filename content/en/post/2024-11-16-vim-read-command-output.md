---
title: "`:read` the output of a command into the current buffer"
date: 2024-11-04T12:09:56-03:00
tags: ["vim", "neovim", "vi", "tips", "TIL"]
featured_image: /assets/article_images/2024-11-04-some-vim-tips/wq-tattoo.webp
description: ""
---

If you want to use the output of a command inside your file, you don't need
to exit Vim, run the command, copy the output, return to Vim and paste the
contents. You can use `:read` (or abbreviated to `:r`) and run a command
with `!`. For example, `:r !ls -a` will insert the output of `ls -a` at
the current cursor position.

You can also insert the content of another file with `:r`, except this time
you don't use `!`, just the file name. For example, `:r second_file` will
insert the content of `second_file` at the current cursor position.

