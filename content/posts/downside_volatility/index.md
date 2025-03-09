+++
date = '2025-03-09T16:51:25-04:00'
draft = false
title = 'Downside Volatility'
tags = ['AWS', 'Crypto', 'AI', 'Technical Analysis', 'Trading Bot']
+++

![Downside Volatility](/images/downside_volatility.png)

This week marked a significant push forward in my suite of digital projects, with substantial work focusing more on the trading components of the project. I began to notice a lot of statistical outliers in recent data I'd been producing compared to testing results from last year. The latest problems started with a sharp uptick in unpredictable market events outside of normal behavior. This led me to realize my algorithm, while performing well on technical analysis signals, was not performing well when the market was being driven by external events. Part of this is due to the fact that I have not yet weighed in real world events into the algorithm. At the moment, those two data streams are still separate, but I plan on adding this in the coming weeks after I've fully built out the AI model and endpoint deployment process. To begin this week's journey, I dug into this problem by first trying to understand the current landscape of algorithm trading and seeing if others were experiencing similar observations in their trading data.

## Market Volatility Impacts Algorithmic Performance

I dedicated several days to researching the current landscape of algorithm trading, specifically examining how market volatility impacts algorithmic performance. The findings were eye-opening: most algorithms are producing increasingly poor results within the last 90 days due to unpredictable economic policy announcements.

Diving deeper, I analyzed performance data from six different trading algorithms across three major crypto exchanges. The data revealed a consistent pattern – algorithms that excelled during stable market conditions showed a 37-42% performance degradation during periods of policy-driven volatility. This wasn't just about reduced profits; the fundamental prediction mechanisms were failing.

Traditional technical analysis relies heavily on pattern recognition within historical data. However, when external events create sharp, unpredicted price movements, these patterns become less reliable. The timing of these events – often outside market hours or announced with minimal notice – creates edge cases that standard algorithms simply aren't designed to handle.

## Fighting Downside Volatility

Based on these insights, I upgraded the base technical analysis algorithm with enhanced logic specifically targeting falling price scenarios. I couldn't just move on to AI model development again without first correcting the algorithm that fuels the AI training process. The technical implementation involved:

1. Adding a dynamic sensitivity adjustment based on detected market volatility levels
2. Implementing a circuit-breaker mechanism that temporarily halts trading when price movements exceed certain thresholds
3. Creating a separate evaluation pipeline for potential trades during detected downtrends, with more stringent profit requirements

The code modifications required refactoring the main decision tree to incorporate these additional control paths. I also had to optimize the volatility detection logic to minimize latency – the system needs to respond quickly during rapid price movements.

Testing showed a reduction in low-profit trades during simulated market downturns. More importantly, the system now accurately identifies a greater rate of scenarios where sitting out is more profitable than participating. While most are complaining about the recent degradation in performance for their algorithms, this turned into quite the opportunity by finally being able to start working off of data with sharp unforseen crashes. Thankfully I'm still just simulating data, so I can keep testing and tweaking the algorithm until I'm confident it's ready for the real world.

## Real-Time Monitoring System Development

Previously, I relied on manual Python scripts that I had to run ad-hoc for backtesting, making the process cumbersome and time-consuming. This was frustrating and slow to constantly re-run manually. So, I decided to build a monitoring system that would allow me to visualize the algorithm's performance in real-time. This system would always run in the background and update the visualizations as new data came in.

The technical implementation involved:
- Creating a local containerized interface that pulls data from S3 tables
- Implementing a data transformation layer to normalize metrics from AWS infrastructure
- Building a visualization framework that renders key performance indicators
- Developing alerting mechanisms for predefined anomaly conditions

The most challenging aspect was adapting to Python-based visualization frameworks. Despite my extensive experience with React and JavaScript for web interfaces, creating visual dashboards in Python required learning new paradigms and libraries. This represented a significant learning curve, as I needed to translate my UI/UX knowledge from the JavaScript ecosystem to Python's visualization tools while ensuring the interface remained intuitive and responsive.

With this monitoring system in place, I can now visually analyze execution paths through the algorithm across different time periods. The containerized nature of the tool means I can run it locally without depending on external services beyond the AWS metrics and S3 data it consumes. The monitoring is able to show me historical results from backtesting that constantly update on a daily basis, live trading data from the trading simulator running in the cloud, and even real time data from the live market. It's also able to generate reports are highlight patterns it picks up from the algorithmic performance data. This has already revealed several optimization opportunities that weren't apparent from examining raw logs alone.

## Backtesting Infrastructure Improvements

The backtesting script improvements centered around dynamic trading interval functionality. Previously, testing different timeframes (1-minute, hourly, 8-hour intervals, etc.) required manual reconfiguration and separate test runs.

The technical solution involved:
1. Refactoring the time-series data handling to support dynamic resampling
2. Creating a parameter-driven testing framework that can execute multiple configurations in parallel
3. Implementing a results aggregation layer to normalize metrics across different timeframes
4. Adding visualization tools that highlight performance differences between intervals

This required significant changes to the core data structures, as the system now needs to maintain multiple temporal views of the same underlying data. The optimization challenges were substantial – naively implementing this would have increased memory usage by a lot and my computer can't handle things like it used to these days. I thankfully had some help from our dear friend Claude who was able to optimize the codebase a bit more efficiently with my hardware.

By the end, I ultimately implemented a lazy evaluation approach that generates temporal views on-demand rather than precomputing them. My fan doesn't come on when the container starts running anymore, so that's a good sign.

## Sagemaker Deployment Challenges

The most frustrating technical challenge this week involved deploying my AI model as a serverless endpoint using AWS Sagemaker. Despite having a well-functioning model locally, the deployment process revealed numerous integration issues.

Specific technical hurdles included:
1. Container compatibility problems between local development environments and Sagemaker's runtime
2. Memory allocation issues when processing large batch prediction requests
3. Cold start times killing the endpoint before it had a chance to fully come online

What made this particularly challenging was that my endpoint would deploy without errors in the logs, but still fail to start because it timed out after 3 minutes. Here's a fun fact about serverless endpoint start up times, you have 3 minutes. That was fun to find out. I still haven't fully fixed this issue, but I'm working on it. I hope to have this fixed by my next blog post with a lengthier explanation on addressing the issue.

## Next Steps

Looking ahead to next week, I'll be focusing on:
1. Finishing the SageMaker serverless endpoint deployment process
2. Test and evaluate AI inference results with on the fly GenAI workflows
3. With any luck, hopefully I'll start bridging real world event detection with AI-based inference results from one of my models

Thanks for reading!