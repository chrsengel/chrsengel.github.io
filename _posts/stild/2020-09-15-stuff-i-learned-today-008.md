---
title: Stuff I learned today 008
date: 2020-09-15 22:00:00 +0200
categories: [stuff i learned today]
tags: [stild, deep learning, gan]
---

Did you know that already back in 1990 researchers came up with an adversarial approach to generative models? There is a heated debate about this though.

As some of you might know, I am currently working on my bachelor thesis about "GAN based Morphing Attacks on Face Recognition Systems". I am still in the research phase and today I came across a [blog post by Jürgen Schmidhuber](http://people.idsia.ch/~juergen/deep-learning-miraculous-year-1990-1991.html) about Deep Learning in the early 90s. [In section 7](http://people.idsia.ch/~juergen/deep-learning-miraculous-year-1990-1991.html#Sec.%207), Schmidhuber describes a system of adversarial networks that utilizes a minimax game, similar to the one used in modern GANs that were developed by Ian Goodfellow in 2014. Though Goodfellow denies any similarities, [see his response to Schmidhuber in a talk in 2016](https://youtu.be/HGYYEUSm-0Q?t=3778). I am no expert on this topic but after reading both the post by Schmidhuber and Goodfellow's paper, the approaches certainly sound similar. I would love to read more on this, so if you have any insights, please hit me up on [Twitter](https://twitter.com/chrsengel).

# ImageMagick

If you ever run into the need to convert between file types, to transform images or simply export pages from a PDF you should look into the [`ImageMagick`](https://imagemagick.org/index.php) tool on Linux. I have been using it for many years now and have countless one-line scripts that help me with everyday tasks.

```bash
# convert a single pdf page to png
# always use a high density, otherwise
# the output will be horrible
convert -density 300 source.pdf output.png
```

The first time I came across the tool was when a professor rejected a signature I did using my Microsoft Surface. She explicitly wanted me to print a document, sign it with a pen, scan it and then send it her again. Obviously that is not only a waste of time but of resources. So I came up with a script that worsens the quality of a PDF and makes it look scanned. There is even a great [HackerNews thread](https://news.ycombinator.com/item?id=23157408) from a few months ago about this where some people came up with even better scripts.

This is the one that I used:

```bash
#!/bin/bash
convert -density 300 "$1" -colorspace gray -rotate 0.45 -depth 2 "$2"
```

---

There is no comment section on this blog as it's just static content, but please feel free to hit me up on [Twitter](https://twitter.com/chrsengel) or send me an email to chris@chris-engel.com.
