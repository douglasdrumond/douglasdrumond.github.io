---
title: "Using `o` in visual mode to change direction of selection"
date: 2024-11-04T12:09:56-03:00
tags: ["vim", "neovim", "vi", "tips", "TIL"]
featured_image: /assets/article_images/2024-11-04-some-vim-tips/wq-tattoo.webp
description: ""
---

If you select some lines or characters with `V` or `v` and want to change
the direction of expansion of the selection, type `o`.

For example, suppose you have the following text:

```
Holmes was certainly not a difficult man to live with. He was quiet in his
ways, and his habits were regular.
It was rare for him to be up after ten at night, and he had invariably
breakfasted and gone out before I rose in the morning.
Sometimes he spent his day at the chemical laboratory, sometimes in the
dissecting-rooms, and occasionally in long walks, which appeared to take him
into the lowest portions of the City.
Nothing could exceed his energy when the working fit was upon him; but now and
again a reaction would seize him, and for days on end he would lie upon the
sofa in the sitting-room, hardly uttering a word or moving a muscle from
morning to night.
On these occasions I have noticed such a dreamy, vacant expression in his eyes,
that I might have suspected him of being addicted to the use of some narcotic,
had not the temperance and cleanliness of his whole life forbidden such a
notion.
```

Suppose your cursor is in the line starting with _Sometimes_. You pressed `V`
and started selecting down with `j`. Then you realised you should have started
from the line _It was rare_ two lines above your initial choice. If you press
`k` to move up, you deselect what you had selected. However, you can type `o`,
the cursor changes to the beginning of selection and now when you type `k`,
you expand the selection upwards.

_Photo by the author_

