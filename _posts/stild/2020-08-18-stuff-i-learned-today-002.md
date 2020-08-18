---
title: Stuff I learned today 002
date: 2020-08-18 19:17:00 +0200
categories: [stuff i learned today]
tags: [stild, linux, ai]
---

This is the second post [of this series](https://chris-engel.com/categories/stuff-i-learned-today/) and today it comes with a fun fact about the first GAN ever built, a discussion about consciousness in AI and some linux tips!

# Some interesting stuff

## Podcast about consciousness in AI

I watched the podcast episode of Lex Friedman with Christof Koch, who is an established neuroscientist, about consciousness in AI[^fridman-podcast]. It is a great discussion about some questions that no one has any answers to yet. Probably because they seem so philosophical.

In Koch's opinion, consciousness is all about experience and he makes a great distinction between intelligence and consciousness:

- Intelligence is about function, adaptation and the ability to learn and understand
- Consciousness is simply about subjective experience

I am quite ashamed to admit that I have never really heard of this area of research. But I am really intrigued by the idea to define and measure consciousness in AI. There is another talk by Koch about "The Sciences of Consciousness"[^koch-talk] that I listened to in order to get a better understanding of the topic.

I found the podcast through a twitter thread by @maraoz[^maraoz-twitter].

## Fun fact about GANs

- Ian Goodfellow wrote the first generative adversarial network in just a few hours over night[^youtubegf].

# Linux stuff

## Compression

If you're in need of extreme compression for your files, then look no further! There's a tool called `lrzip`[^lrzip] that helps you out. I successfully halved some folders that I previously compressed with `tar`. The tool works best with documents.

For maximum compression use the `-z` option. It does not work for media files however. I tried compressing a 15 GB raw image folder and only got it to ~14.8.

Here's a quick comparison between the regular `tar cfvz` compression and `lrztar -z` on a directory full of documents.

![Compression Comparison]({{ "/assets/img/stild/2020/08-18/comparison.png" | relative_url }})

Thanks to lrzip I could save more than a gig in my Dropbox folder. It should be noted though, that using the tool on large directories will take a **long** time. The 15 GB test took more than 30 minutes on my Thinkpad T480.

## Sorting by size

Today I wanted to find out what the largest files and folders were in a directory. Interestingly enough I could not find a quick solution online that would not list files and directories sorted separately. So I tried some commands and came up with the following structure: `du -hs * | sort -rh`.

(Also, reading man pages sucks!)

`du -hs *` lists the files and folders in the current folder, `sort -rh` sorts the columns by size. The `-h` flag stands for `--human-numeric-sort`. The `-r` flag will sort the output in descending order.

# Footnotes

[^youtubegf]: [Andrew Ng's interview with Ian Goodfellow](https://youtu.be/pWAc9B2zJS4)
[^fridman-podcast]: [The podcast on YouTube](https://www.youtube.com/watch?v=piHkfmeU7Wo)
[^koch-talk]: ["The Sciences of Consciousness: Progress and Problems" on YouTube](https://www.youtube.com/watch?v=4gT-1S3FO4s)
[^maraoz-twitter]: [Short twitter thread by @maraoz](https://twitter.com/maraoz/status/1295087553796874240)
[^lrzip]: [lrzip Github repo](https://github.com/ckolivas/lrzip)
