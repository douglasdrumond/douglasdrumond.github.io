---
title: "The `:normal` command in Vim"
date: 2024-11-04T12:09:56-03:00
tags: ["vim", "neovim", "vi", "tips", "TIL"]
featured_image: /assets/article_images/2024-11-04-some-vim-tips/wq-tattoo.webp
description: ""
---

You can use `:normal` (or the abbreviated form, `:norm`) in Vim to execute
a normal command on a range of lines.

Example:
```
:%norm I1. <cr>
```

Here, `<cr>` means 'press enter key'. Also, notice the space after the dot.

That command will act on all line (`%`) and insert at the beginning of the line (`I`)
the number 1 followed by a dot, followed by a space.

After pressing enter, the command is executed and Vim returns to normal mode.

You can type control characters by using `ctrl-v`, as explained in the [next
tip]({{< relref "2024-11-04-vim-ctrl-v" >}}). For example, if you want to surround
lines 2 to 7 with quotes:
```
:2,7norm I"^[A"<cr>
```

Here, `^[` does not mean "caret + open square braces", it's `ctrl-v` followed by `esc`.

_Photo by the author_

