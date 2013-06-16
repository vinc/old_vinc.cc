---
layout: post
title: "Adding and subtracting numbers in Vim"
date: 2013-05-13 19:45
comments: false
categories: [Tips, Vim]
---

Using Unix as an IDE means accumulating a vast amount of tips about improving
efficiency on specific tasks. Most of them are short, yet worth sharing, thus
this blog post about two key bindings in [Vim][1] for manipulating numbers.

<!-- more -->

The `ctrl-a` and `ctrl-x` commands will respectively increment and decrement
the next number in a line without having to go into insert mode, saving
multiple keystrokes when playing [VimGolf][2].

As mentioned by the documentation (`:help ctrl-a`), those commands can also be
useful in a macro. The simplest example would be to perform an addition on a
number:

1. `qa` - Start recording into register `a`.
2. `ctrl-a` - Increment the number.
3. `q` - Stop recording.
4. `<n>@a` - Add `<n>` to the number.

By default Vim will also recognise number from octal and hexadecimal numeral
systems and transform them accordingly:

> Octal - If included, numbers that start with a zero will be considered
> to be octal. Example: Using `ctrl-a` on '007' results in '010'.
>
> Hex - If included, numbers starting with '0x' or '0X' will be considered
> to be hexadecimal. Example: Using `ctrl-x` on '0x100' results in '0x0ff'.

See `:help nrformats` in Vim for more information.

[1]: /blog/categories/vim
[2]: http://vimgolf.com
