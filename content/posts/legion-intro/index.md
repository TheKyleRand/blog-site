+++
date = '2025-05-11T12:50:42-04:00'
draft = false
title = 'Building Legion: Conversation as Computation'
tags = ['AWS', 'Crypto','Trading Bot', 'Legion']
+++

{{< audio src="audio/legion_intro.mp3" >}}

![Featured Image](/images/featured_image.png)
I ran into a little bit of a problem with my crypto platform. Actually, scratch that—it was a lot of problems. Like, hit-every-red-flag-in-the-diagnostics kind of problems. So I started untangling it all. And then I realized, the problem wasn't in one place. It was everywhere.

If you've built any kind of algorithmic system, you already know the holy grail is adaptability. Dynamic weights, self-adjusting formulas, smarter heuristics that can keep up with shifting market conditions. Maybe RSI doesn’t cut it in a choppy market, so you swap it out with a momentum indicator. Or you lean into mean reversion when the volatility dries up. Small tweaks, same skeleton.

Except in crypto? Not so simple. The market doesn't just change; it transforms. And if your algorithm morphs too? Then your backtests are invalidated. I was essentially building and backtesting a new trading system every single day. Combine that with retraining AI models daily, and by the time you finished one model, it was already stale. Multiply that across 24 hours, and the AWS bill alone could give you a heart attack.

But things got really messy when I tried to inject real-world events into the formula. I thought, hey, what if I weighted the model based on external events—regulations, announcements, political noise? It seemed smart on paper. In practice, it was chaos.

There’s no universal truth in crypto news. A new regulation might be great for me and a total disaster for someone else. I tried to encode these scenarios—used generative AI to simulate outcomes, then tried to score them. It became a ranking system of subjectivity, trying to quantify human nuance with math. It didn’t work. It was brittle, shallow, and incredibly naïve.

So I took a step back. And then another. Until I was staring at the old architecture diagram I posted a while ago. And I saw something pretty eye-opening. I had built a strong foundation for what could’ve been a robust trading platform. But I’d been asking it to do the impossible—predict the future with tools designed for the past.

That’s when I scrapped it. All of it. I needed something different. Not just a smarter algorithm or faster AI. I needed a whole new approach.

### Enter Legion

What I’ve started building now is something I haven’t seen before. You know that character Legion from the comics—or maybe the FX series? One mind, thousands of voices, each with its own personality and agenda. What if that concept wasn’t just great sci-fi, but a blueprint for how decision-making systems could work?

Why rely on a single system to make a decision, when you can have multiple agents talking it out? What if system A wants to buy based on MACD, but system B sees something off in the volume? Instead of choosing one or the other, what if they debate?

That’s how I ended up in multi-agent territory. What’s often called Agent-to-Agent architecture, or A2A. Each agent specializes in something—one reads technical indicators, another parses news sentiment, another evaluates trend strength. Alone, they're limited. But when they talk to each other? That’s where the magic starts.

But I didn’t stop there. Traditional trading bots are event-driven—price hits a threshold, an indicator fires, a trade is triggered. Legion doesn’t work like that.

Legion doesn’t wait for a buy signal to wake up and do something. It doesn’t run in response to a condition being met, like a candle crossing above a moving average or RSI hitting oversold territory. Most algorithmic trading systems, even advanced ones, follow this paradigm. An event occurs, and the code responds. That’s called event-driven architecture. The entire structure is built around discrete triggers that fire off actions.

But Legion doesn’t have events. It doesn’t sit idle waiting for a condition to be true. It’s always awake. Always watching. Always thinking. Its presence in the market is persistent, not conditional.

This fundamentally changes how decisions are made. Traditional systems wait for confirmation before making a move, often defined by predefined thresholds or historical backtested probabilities. Legion doesn’t wait for a perfect entry. It starts from the assumption that it's already “in” the market. Not necessarily in a position, but present in the flow of data and decisions. Even if it hasn’t placed a trade, it's already participating in the market’s dialogue through continuous observation and inter-agent conversation.

This also redefines what an “entry point” means. There isn’t one. Legion’s entry point is the moment I turn it on. That’s it. From that point forward, it’s not evaluating “should I enter now?” the way traditional bots do. It’s maintaining an ongoing state that could result in a trade—or not—depending on the evolving consensus between agents.

It’s not reacting to a market condition. It’s immersed in it.

This creates a level of autonomy that most trading systems don't have. Event-driven bots respond to stimuli. Legion behaves more like a trader who's actively watching, constantly weighing decisions, sometimes holding back not because a signal didn’t appear, but because the conversation between agents hasn’t reached agreement. Or maybe the agents reached consensus that the best action is inaction. That subtle distinction—deliberate inaction versus absence of signal—is huge. It gives Legion a sense of presence in the market that doesn't hinge on a single threshold being met.

It doesn’t ask “has something happened yet?” It’s already in the thick of it, constantly asking “is now the moment to act, or do we wait?” That shift—from reacting to participating—is what makes Legion feel less like a script and more like an entity.

### Conversation as Computation

What makes Legion different isn't just that it's a group of agents—it’s that those agents are capable of talking to each other in a real, structured, purposeful way. I’m not talking about a shared memory or passing variables around. I’m talking about literal conversations. Natural language. Prompts. Dialogue between agents, where each one has its own specialty, its own perspective, and, crucially, its own responsibilities.

Here’s the kicker: in Legion, agents don’t just respond to prompts—they issue them. Any agent can fire off a message that becomes the prompt for another agent. And they’re not just passing along passive data either. The agents have access to tools—functions, APIs, scripts, even cloud-native workflows. When one agent wants to understand something outside its scope, it asks another agent that’s better suited to the task. And when it reaches a point where action is required, it doesn’t just say, “someone should do something.” It calls the function directly—or asks the appropriate agent to do it.

This setup means that “thinking” and “acting” are inseparable in Legion. If an agent identifies a concern with market volume, it might ask the news sentiment agent, “Did something just happen to explain this?” The news agent parses its own datasets and replies, “Yes, the SEC just announced something.” From there, the governance-risk agent might chime in, “This type of announcement historically causes a 2% drop within the hour—should we reconsider the current trade posture?”

You can see where this is going. The agents effectively use each other as both context providers and as tools. One agent’s output becomes another’s input, and the flow doesn’t stop unless someone—meaning one of the agents—decides that consensus has been reached or that a deadlock needs breaking.

The way this is wired together is honestly kind of beautiful. Every agent has access to a shared toolkit: real-time data feeds, historical price movement patterns, on-chain activity monitors, regulatory news aggregators, you name it. But not every agent knows how to use every tool. Instead, they ask each other. They talk. It’s not just computation—it’s conversation-as-computation.

And that conversation can result in function calls. The agents can call APIs, evaluate predictions from GenAI models, or even reach out to a Lambda function to simulate a trade before recommending it. That makes them powerful. But it also makes recursion a very real problem. One agent calls another, who calls another, and suddenly you’ve got a loop that never ends. That’s why Legion also has supervisory agents—watchdogs designed specifically to monitor the flow of conversation, detect when agents are spinning their wheels, and intervene. These aren’t just rules written into code. These are agents whose entire job is to prevent the rest of the system from collapsing into a loop.

It’s a massive departure from anything I’ve built before. Traditionally, you code the logic yourself and you’re responsible for every edge case. With Legion, you delegate logic. You equip agents with tools, guardrails, and instructions, and then let them handle the conversation themselves. That changes everything about how decisions are made. It’s no longer: "if condition, then trade." It’s now: "let’s talk about the data, make sense of it together, and only act when we agree."

### What’s Next

I’m working on a standardized agentic framework. Every agent will have system-level instructions, but I’ll also be creating shared prompt scaffolding to keep their conversations grounded. It’s a strange balance—fostering improvisation while still enforcing trust and truth. But I think it’s possible.

Oh, and the weekly blog schedule? Yeah, that's not happening anymore. There’s just too much going on between work, life, and projects like this. But I’ll post when it matters.

Next time, I’ll break down how I’ve structured the agent instructions, and how to get agents to improvise without making things up. It’s a little messy. But if it weren’t messy, it wouldn’t be new.
