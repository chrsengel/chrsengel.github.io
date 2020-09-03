---
title: My First Proper Deep Learning Model
date: 2020-09-02 22:00:00 +0200
categories: [deep learning]
tags: [fastai, deep learning]
---

Today I trained my first proper Deep Learning model with the help of FastAI. I recently started the brand new FastAI 2020 course[^fast] and so far it has been an amazing experience. If you read my other posts before, you know that I am reading the Deep Learning Book by Ian Goodfellow[^book] in parallel. While the book focuses on the theoretical part of Deep Learning, I have been eager to finally get my hands dirty. FastAI is perfect for this as it provides **extremely** simple python libraries for the practical use of Deep Learning models.

# Objective

The goal of my model is to distinguish between two types of squirrel species. I chose the following:

- Eastern Gray squirrel
- Red squirrel

| Eastern Gray Squirrel                                                                                     | Red Squirrel                                                                        |
| --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| ![Eastern Gray](https://cdn.pixabay.com/photo/2019/10/29/13/19/eastern-gray-squirrel-4586908_960_720.jpg) | ![Red](https://cdn.pixabay.com/photo/2018/03/21/16/30/squirrel-3247305_960_720.jpg) |

The task might seem rather simple to a human, as both are simply characterized by having different colors. But in practical conditions there might be challenging light conditions that affect the appearance and there might be lots of surroundings, like woods and bushes, that might distract a deep learning model. Even I remember having trouble distinguishing them in nature.

# Gathering Data

Before I started the FastAI course, I was always under the impression that gathering the necessary training data would come at a large resource cost of both time and money. But it turned out to be free and extremely fast. I simply had to grab a free Bing Image Search API key, use the provided fastai library, specify the search terms and download the data. Granted, the data set only contained 150 images for each squirrel type but the whole process took less than a minute! And as we will see, the small dataset provided impressive results.

## Cleanup

Before I started the training process I manually went through the image files and cleaned up the data set. Considering how fast the total model training process was, the cleanup took more than 90% of the time.

The course recommends another way to clean up data sets. It seems rather unintuitive, but the approach is to first train a model using the uncleansed data and then let it show you the data that it struggles with. Most likely these images will contain wrong labels or depict other random stuff. In my case I had a lot of comics that had to be removed.

# Training

Training was a blast. The fastai library is extremely simple, but powerful. I have written some pytorch code before and always had to write a lot of boilerplate code. With fastai, you can compress dozens of lines of code into a single function call.

```python
learn = cnn_learner(dls, resnet18, metrics=error_rate)
learn.fine_tune(4)
```

These lines of code declare a pre-trained convolutional neural network that is fine tuned with four epochs of the training data. Under the hood it uses the resnet model with 18 layers. It is a really small and fast model but provided impressive results later on. `dls` is the `DataLoaders` object that contains the training and validation data.

# Results

The first run was not very promising. I got an error rate of around 7%. After a quick investigation I saw that the data set was still not fully cleaned up. Some of the labels were still incorrect. After fixing the issues I trained the model again and the results were astonishing!

| epoch | train_loss | valid_loss | error_rate | time  |
| ----- | ---------- | ---------- | ---------- | ----- |
| 0     | 0.521670   | 0.112777   | 0.017241   | 00:27 |
| 1     | 0.367291   | 0.117923   | 0.068965   | 00:30 |
| 2     | 0.280987   | 0.031929   | 0.000000   | 00:30 |
| 3     | 0.219196   | 0.017877   | 0.000000   | 00:30 |

With only four epochs and a rather small pre-trained model I accomplished to train an almost perfect distinguisher for squirrels! And it really proved itself on previously unseen images of squirrels.

# Takeaways

Since I first read about AI and Deep Learning, I always had the misconception that you needed tons of training data. And for real-world applications, particularly ones where Deep Learning had not been applied before, my conception was that gathering the necessary data needed a ton of manual work. Therefore I was under the impression that Deep Learning proved rather impractical.

Granted, distinguishing squirrel species is not a great example for the practical use of Deep Learning, but given the amazing (and oftentimes free) tools, developers these days have access to, I completely changed my mind. I got free access to millions of images and in total I needed less than 150 images for each squirrel type to get a near-perfect model. That is just mind blowing.

I also learned that the act of cleaning the data is still very labor intensive. I really wonder how large corporations and new Startups solve that issue in production. I have plenty of ideas about the practical use of Deep Learning, especially for cyber security purposes, but I can't really imagine yet how the process would look like to manually clean up humongous datasets.

# Footnotes

[^fast]: [FastAI 2020 course](https://course.fast.ai)
[^book]: [Deep Learning Book](https://www.deeplearningbook.org/)
