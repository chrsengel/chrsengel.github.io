---
title: Stuff I learned today 005
date: 2020-08-27 19:00:00 +0200
categories: [stuff i learned today]
tags: [stild, dart, reading]
---

Today with generator functions in Dart, Melatonin and a couple of interesting articles I read.

# Stuff I learned today

## `yield`

`yield` is a generator function in Dart. It can be used to output multiple values to a stream[^yield-doc]. I found this to be particularly useful while implementing the BLoC pattern in an app I was working on. By using `yield` you can use a single event to generate multiple state changes.

- the `yield` keyword in flutter

## Melatonin

I have long had the feeling of having a bad sleep cycle as I read and work until late in the evening and am often tired during the day. Since I got a new Galaxy Watch two weeks ago I have continuously tracked my sleeping patterns and it's astonishingly worse than I thought. On average, I sleep around 4-5 hours a night. Surprisingly it did not help to go to bed earlier. I just lie there and cannot fall a sleep. So I did some research and came across the Melatonin hormone.

Melatonin is a natural hormone that is jointly responsible for the synchronization of the sleep cycle. The body naturally produces the hormone in the pineal gland in the brain mainly during the darkness and stops production if light hits the eyelid[^melatonin]. Naturally, humans have high melatonin levels during the evening which prompts them to become tired.

I think here lies the problem. During the day I am primarily inside. As there is currently a heat wave going through Europe, I keep the roller shutters down during the day. I usually work on bright monitors or read on a bright devices at night. I always use the night mode on all devices that support it but this does not seem to have any positive effect.

I am going to undertake a small experiment. This week I will try to get outside for at least 30 minutes during the day and stop working and reading on bright devices after 10pm. Will probably do another post solely about the topic with some nice graphs, so stay tuned!

# Stuff I read today

- I am currently figuring out how to let users upload files to an AWS S3 bucket. I found a medium article[^medium] that explains the concept of presigned urls very well. Alongside the official documentation[^aws] this made it easy to implement the feature in little to no time.
- Reading through the HackerNews comments on the launch of Dropbox is a treat[^hn-dropbox].
- Read the story about 'The Greatest Investor You've Never Heard Of'[^investor].
- Read about the greek philosopher Diogenes, who was 'a controversial figure' and one of the founders of Cynic philosophy. If you want to read some crazy stories that will make you laugh, check out the wikipedia article[^diogenes].
- Read about the 'Flow and Happiness'[^flow].

# Footnotes

[^yield-doc]: [Flutter Documentation](https://dart.dev/guides/language/language-tour#generators)
[^medium]: [Medium post on S3 image uploads](https://medium.com/udroppy/handling-thousands-of-image-upload-per-second-with-amazon-s3-7a1009e8ffc4)
[^hn-dropbox]: [Dropbox launch on HN](https://news.ycombinator.com/item?id=9224)
[^aws]: [AWS Docs on presigned URLS](https://docs.aws.amazon.com/AmazonS3/latest/dev/PresignedUrlUploadObject.html)
[^melatonin]: [Melatonin explained](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4334454/)
[^investor]: [The Greatest Investor You’ve Never Heard Of - Article on forbes.com](https://www.forbes.com/sites/maddieberg/2019/02/19/the-greatest-investor-youve-never-heard-of-an-optometrist-who-beat-the-odds-to-become-a-billionaire/amp/)
[^diogenes]: [Wiki article about Diogenes](https://en.wikipedia.org/wiki/Diogenes?wprov=sfla1)
[^flow]: [Flow and Happiness](https://www.psychologytoday.com/us/blog/one-among-many/201502/flow-and-happiness)
