---
title: Stuff I learned today 009 - Github Actions
date: 2020-09-22 22:00:00 +0200
categories: [stuff i learned today]
tags: [stild, ci]
---

Today I learned how to set up a Github Action that publishes docker images on every commit to the main branch. The configuration is very simple and if you are used to defining pipelines in Jenkins you will see a lot of similarities.

First, you need to define the name of the action, define the event triggers in the `on` section and then the jobs you want to run. There can be multiple event triggers and multiple jobs with multiple steps each.

In this case I created an action to push Docker images to Docker Hub. Thankfully there is a pre-defined action you can use that simplifies the process even more.

```yml
name: Push to Docker Hub
on:
  push:
    branches:
      - main
jobs:
  push_to_registry:
    name: Push Docker image to Docker Hub
    runs-on: ubuntu-latest
    steps:
      - name: Check out the repo
        uses: actions/checkout@v2
      - name: Push to Docker Hub
        uses: docker/build-push-action@v1
        with:
          username: $\{\{ secrets.DOCKER_USERNAME }}
          password: $\{\{ secrets.DOCKER_PASSWORD }}
          repository: chrsengel/pytorch-gans
          tag_with_ref: true
```

> Note that I had to add the backslashes to the `username` and `password` because the build script for this blog would otherwise try to enter these environment variables.
