---
title: On My Total Failure
date: 2020-08-18 19:50:00 +0200
categories: [startups]
tags: [failure, dethlify]
---

A few months ago I launched a blockchain-based product, called [Dethlify](https://dethlify.com). The purpose of Dethlify is to manage a person's digital inheritance in a trustless way by using smart contracts on Ethereum through a beautiful and intuitive interface. In principle it works like this: A user defines their heirs, the tokens they want to leave behind and an inheritance rate for each heir and token. This information is stored in a program on the blockchain and the users can do some fancy stuff with it, like interacting with other financial applications on the network.

When I came up with the idea I initially thought, "hey I need this, others probably want it too!". So I built it. I had already built a prototype just for myself a year earlier so I didn't spend much time talking to others and just built the thing over many weeks, spending countless nights at the desk, until it was ready to publish.

![Dethlify History](/assets/img/dethlify-github-history.png)

Once the first version was done, I went to the Ethereum Community Conference in Paris and talked to a bunch of people, trying to get them to use it. And I **absolutely failed** to excite them. My confidence began to crumble as some of the people I talked to didn't understand how it worked or did not seem to be interested at all in the idea of managing inheritance through a trustless program. Some thought the website sucked and some pointed me to other big players in the market that seemingly provided the same features (which in fact they do not).

Already then, I came to the realization that this was probably not going to work out. But I kept going, modifying the underlying Smart Contract to enable more DeFi integrations and polishing the website. If I build it better, people will come, right? No. In total, only around 14 people used it, 4 of which were my friends who only used it once and most of the other ones only deployed contracts on the supported testnets.

# Why Did I(t) Fail?

After sleeping on it for a while and talking to more people outside the field, I came to the conclusion that I made four essential mistakes right from the get go:

1. I started building without verification.
2. I did not do enough research.
3. I built a product in a teeny tiny niche market.
4. I did not know the channels to get the necessary exposure.

## Verify Your Ideas

Of course I had read many of the StartUp books before I had started working on Dethlify. It has been my lifelong dream to build a successful company and I started my first endeavours when I was 14 years old - back then through Blogger.com. I read a ton about how to verify ideas, the many methods one can use to do so and I know the most important rule: not to build stuff without knowing the customer.

And I still did not follow these rules. I thought I knew it better and ultimately, I thought, if I have the problem, then more people probably have it too. This holds true[^linda-xie-tweet][^other-tweet], but does not guarantee that they will use your product in the end.

## Do Your Research

You probably know the feeling of starting a new project. You are excited to start planning, start coding, start setting up your environments and simply be creative about something that is important to you.

I did not spend much time on research. I simply googled some of the key features I thought my application should have and could not find any competitors. I took that as a "here's my chance - no need to google more" card and did not bother to look for similar applications.

At that time I did not know that most of the people I talked to thought, that a product that I had used myself for over a year already, was a competitor to my service. A simple search query with different parameters could have shown me the confusion early on.

But as you are bringing your idea to life, you have an exact understanding of what it does and does not do. You need to "think outside the box" and try to see your product through the eyes of someone who has no idea about it. The key is research and talking to potential customers.

## Check The Market

I also did not waste a full minute to calculate the total addressable market. I had no idea at first how to make this service profitable. I am still a student who works part time at another job, founded a company for about 400€, so I did not really worry about financial details in the short term. But I should have done exactly that. As I soon found out, the total addressable market is insanely small and way too small for a service like Dethlify to be profitable:

Currently, there's only around 2,900 applications on Ethereum and only about 50,000 people actively use the network[^june-numbers]. Compare that to the billions of smartphone users. Most of them also only have tiny amounts of money in their wallets[^glassnode]. What I did not realize when I started: Dethlify only makes sense if you have large sums of money that you want to protect from loss. If we target these users, then the total number of approachable users is in the low hundreds[^glassnode].

If I were to start all over I would definitely spend a lot of time on market research. Nowadays, tools like glassnode or simply sites like [ethhub.io](https://ethhub.io) can provide great insights into the Blockchain market.

## Know Your Channels

After I had launched new versions of the product, I posted about it a couple of times on Twitter and wrote many DMs to people I knew who were interested. None of them bothered to register.

In hindsight, I should have been way more confident and should have posted on more platforms other than Twitter, like Reddit, HackerNews, Discord and other channels.

I simply did not know where to launch and get the most exposure. I only recently got into the many DeFi Discord channels that have thousands of active users. I only have around 130 Twitter followers so I need to step up that game and know my distribution channels!

# Outlook

I will soon shut down Dethlify. The site has not seen traffic in days, there is simply no demand and it is just not economically viable in such a small niche market - at least for now. I am confident that the market will keep growing and perhaps in a few years it is worth a shot to build something comparable and release it to the wild. I also have a ton of other ideas that I want to work on and I am currently looking into verifying some of them.

# Takeaways

So, after reading all this you might be thinking "of course that went south!". Well, I learned my lesson. I am still incredibly happy to have built the product all by myself and I had a ton of fun building it. It's a fully working system with many components, such as

- the Smart Contracts[^dethlify-contracts]
- the React interface with lots of routes, custom hooks, tons of custom components and about 25,000 lines of code
- a backend consisting of multiple custom docker containers with another 20,000 lines of code and
  - two databases (neo4j and mongo)
  - custom worker queues (using nodejs, bull and redis)
  - email services using AWS SES
  - fancy bash scripts that glue everything together

I have learned so many things from this project. And ultimately building companies is based on learning from failure. At least that's what the consensus seems to be. I am more than confident that my next endeavours will have a much higher chance of success because of the experiences I could gain through this project.

---

There is no comment section on this blog as it's just static content, but please feel free to hit me up on [Twitter](https://twitter.com/chrsengel).

# Footnotes

[^linda-xie-tweet]: [https://twitter.com/ljxie/status/1261711895662194688](https://twitter.com/ljxie/status/1261711895662194688)
[^other-tweet]: [https://twitter.com/itaidamti/status/1261713962875281408](https://twitter.com/itaidamti/status/1261713962875281408)
[^glassnode]: [Glassnode insights (needs a free account)](https://studio.glassnode.com/metrics?a=ETH&m=addresses.MinPoint1Count)
[^june-numbers]: [https://consensys.net/blog/news/ethereum-by-the-numbers-june-2020/](https://consensys.net/blog/news/ethereum-by-the-numbers-june-2020/)
[^dethlify-contracts]: [Dethlify Contracts](https://github.com/dethlify/dethlify-contracts)
