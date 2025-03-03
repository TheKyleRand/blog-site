+++
date = '2025-03-03T12:15:30-05:00'
draft = false
title = 'Merging Architectures into a Suite'
tags = ['AWS', 'Crypto', 'AI', 'Technical Analysis', 'Trading Bot', 'Crypto Compass', 'Crypto Newspaper']
+++

It's been a while since I posted on LinkedIn. I thought I'd be able to keep up with a weekly release schedule, but then the following happened:
- Foreign economic policies kept getting announced and flip-flopped causing the algo to go haywaire for a bit
- Prices recently went parabolic in the crypto market, though not in a great way
- I started migrating my entire local setup to AWS, which is a whole ordeal in itself
- I had to go window shopping for datasets
  - I couldn't find any datasets I liked with the right frequency and features, so I had to make my own
    - I had to create my own data pipelines to ensure consistency and reliability of the data getting ingested

Thanks to a co-worker of mine, I also came to the conclusion that raw posts on LinkedIn would limit the amount of information I could share. That led to the creation of this blog site and infrastructure to support it (major shout-out to [Hugo](https://gohugo.io/) for making this whole process a breeze).

So now the question begs, what did I work on since my last LinkedIn post? Well, to summarize it, here's a pretty picture of what I currently have setup in my AWS account now, all of this being built since my last post:

![Suite Architecture](/images/crypto_suite_aws_large.png)

### Merging Architectures
While I was building out Crypto Compass, I noticed I was constantly reusing architecture and scripts from older projects of mine, such as a project that could create an AI generated crypto newspaper based on recent price movements. While I had at one point abandoned this project, I realized I could easily bring it back and launch it on top of the architecture I was already building out for Crypto Compass. I was writing a second application to work on top of this as well, which was an automated crypto trading bot.

This has now led to the complete evolution of what I'm trying to accomplish; an entire suite of applications based on one technical analysis algorithm that I can expand on top of with something as little as a spark of imagination.

So, what do all these projects even do?

#### Crypto Compass
Crypto Compass is built off of a few different price predictors for short-term (and now near-term) price movements. It uses:
- A raw technical analysis algorithm utilizing advanced mathematics to produce a score, prediction, and various other important metrics to keep track of
- An AI Powered version of the same technical analysis algorithm, but it has been trained on historical data in an attempt to provide a more accurate prediction. This model pipeline is also capable of retraining itself on new data, in an effort to keep up with latest market trends.
- An AI powered version of the same technical analysis algorithm, but it incorporates real time news data to provide a more accurate prediction. This output also incorporates the raw non-AI powered algorithm in case the AI model's prediction is too far off from the raw algorithm's prediction, or vice versa. This is really meant to provide a user with various predictions they can choose from, and see how they compare to one another.

#### Crypto Trading Bot
Sitting inside of the AWS Lambda Step Function is now an additional lambda function that uses the output of Crypto Compass' algorithms to make trades on a centralized exchange (CEX); the name of which I will disclose at a later date. This trading bot is able to keep track of a plethora of metrics to ensure efficient trading strategies and lower tax liabilities. I'm very excited to share how this bot works at a later date and will dedicate a whole post to it. What started out as simple buy/sell logic quickly evolved into something much more complex, though I'm still simulating price performance and have not yet given it access to real money. For now, it runs in my AWS account with imaginary funds, but it's exciting to watch every day!

#### Crypto Newspapers
I still can't believe I resurrected this project. I had completely abandoned it late last year, but now it's back and better than ever. This project also deserves its own blog post, so I'll save deep diving into this for another day. However, at a high level, this project uses lives historic price data (really just from the past 24 hours, and any other time in the dataset that is deemed relevant) and uses AI models to generate a newspaper-esque output that can be used by traders to make decisions or just for fun. Utilizing both an AI Image Generator and an AI Text Generator, this project is able to stay self-sufficient and generate a new newspaper every day without any human intervention.

