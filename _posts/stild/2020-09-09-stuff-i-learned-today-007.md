---
title: Stuff I learned today 007
date: 2020-09-09 22:00:00 +0200
categories: [stuff i learned today]
tags: [stild]
---

Today's post comes with aliens, advice for improving writing skills and a Mac OS virtual machine!

# Books 

Two days ago I had a hand surgery and I could not do much coding or typing since then. So I read a lot. Here is some of it.

## The Three-Body Problem

I read the sci-fi novel '[The Three-Body Problem](<https://en.wikipedia.org/wiki/The_Three-Body_Problem_(novel)>)' by Liu Cixin. It is the first part of a trilogy and portrays the first contact with aliens from the Alpha Centauri star system. I do not want to spoiler anything but it is one of the best sci-fi books I have read in a long time. If you are into rationale science fiction with a hunch of history and a focus on physics, then you will love this book. I already purchased the second part.

Throughout the book the author tells many stories and facts about the cultural revolution that happened in China during the sixties and seventies. As I am from Germany, I had never learned anything about the country's history in school. It seems like another universe. Religion, culture and art seem so different. I definitely want to learn more about it. But where should I start?

## Improve Writing Skills

I have always thought about how I could improve my overall writing skills. That is one of the motivating factors behind this blog. I read some books in the past but could not find helpful practical advice so far. Through a friend, I finally found two great (German) books about the subject. And after reading half of the first one, I must confess that I used to make many of the described common errors.

I am not done with those books yet, but here is some of the advices I want to try out in the future. Note that this is primarily target for German speakers.

- Start your writing with an interesting introduction or fact that tempts the reader to read on. Avoid common standard phrases.
- Literal pictures, examples and comparisons are often necessary. Even in scientific papers.
- If appropriate, add a grain of humor to your writing.
- Prefer short, precise words (German is known for the creation of long ambiguous words that are hard to read and often times hard to understand).
- Verbs are the strongest words, adjectives the weakest. Use them accordingly.
- Synonyms should only be used in subordinate clauses, seldom in main clauses. Prefer to use the same nouns multiple times if necessary.
- Anglicisms are not always bad. But make sure to use socially accepted ones and that everyone understands what you are trying to say.
- Stop using buzzwords. Prefer to use the original noun instead of the fancy word.

I am only halfway through the first book ('[Deutsch für junge Profis](https://www.amazon.de/Deutsch-f%C3%BCr-junge-Profis-lebendig/dp/3871346721)') yet, so there will be plenty more lessons learned.

# Tech

## Mac OSX in a Docker Container

As I am currently programming some apps in Flutter but do now own a Mac I am in somewhat of a jam. I cannot test or debug apps for the iOS build. Because of Apples arrogant decision to not release a simulator for other platforms I am forced to buy a Mac if I wanted to release my applications to the App Store. To get around this I have been looking for native virtual Mac OS images. And looks like I finally found one through a friend!

There's a ready to use [Docker container that provides OSX](https://github.com/sickcodes/Docker-OSX). It is based on the [OSX-KVM](https://github.com/kholia/OSX-KVM) that I had previously trouble with running on my machine.

At first I ran into trouble using the wrong permissions for `/dev/kvm`. But once that got fixed it worked! Rather slow at first, but after reinstalling the image and adjusting the resource parameters it runs like a charm. Now I only have to get the iOS simulator working and I am good to go!

Special thanks to [@quambene](https://twitter.com/quambene) and [@th0jest](https://twitter.com/th0jest) for this.

---

There is no comment section on this blog as it's just static content, but please feel free to hit me up on [Twitter](https://twitter.com/chrsengel) or send me an email to chris@chris-engel.com.
