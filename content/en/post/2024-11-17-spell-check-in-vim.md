---
title: "Checking spelling"
date: 2024-11-17T10:09:56-03:00
tags: ["vim", "neovim", "vi", "tips", "TIL"]
featured_image: /assets/article_images/2024-11-04-some-vim-tips/wq-tattoo.webp
description: ""
---

Vim has a built-in spell check that you can enable with `:set spell`. You can
also set the language with `:set spelllang=` followed by the two-letter code of
the language and optionally a dash and the region (e.g., `:set spelllang=en` or
`:set spelllang=en-GB`).

After enabling the spell checker, you can move between different mistakes with
`]s` and `[s`.

I knew about the spell check, I knew Vim highlighted spelling mistakes, and I
knew how to move between the mistakes. I usually fix them manually and I never
bothered to learn how to make Vim fix them for me. Until today.

Press `z=` and Vim will present a list of numbered suggestions. Press the
equivalent number and Vim will replace the mistyped word with the one you
chose. Alternatively, you can use `1z=` to apply the first option without
seeing the list. In fact, you can change the number and use `2z=` for the
second option and so on, but that increases the risk of picking the wrong
option and it's not a useful tip. I presented it here for curiosity and
completeness.

