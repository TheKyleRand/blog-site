+++
date = '2025-03-23T16:05:07-04:00'
draft = false
title = "Vibe Coding with Extra Steps"
tags = ["AI", "Coding", "Best Practices"]
+++

{{< audio src="audio/vibe_coding.mp3" >}}

There’s been a screenshot circulating around LinkedIn recently that sparked a lot of debate. It's from someone claiming they built an entire SaaS with Cursor—zero handwritten code—and then days later, had to go radio silent because of the chaos that followed. People maxing out API keys, bypassing subscriptions, trashing their database. It didn’t end well.

![Vibe Coding Snapshot](/images/vibe_coding_post.jpeg)

What frustrates me most isn’t just that this happened, but that the fallout is being used to imply vibe coding doesn’t work. That it’s inherently reckless. That AI can’t handle complexity. That tools like Cursor or ChatGPT are toys.

The reality is, vibe coding isn’t the problem. Misusing it is. Most people who vibe code, or at least are familiar with vibe coding, would probably agree on its real definition which is that you use an LLM to do everything from start to finish for you. But this technology isn't there yet to be able to create production ready applications within minutes, so if you try to use this technology with that purpose in mind, you're going to set yourself up for failure.

## Vibe Coding Isn't a Shortcut to Done

Let’s get one thing straight—vibe coding shouldn't be about telling an LLM “make me an app” and expecting miracles. That’s how you get junk. Garbage in, garbage out. And that’s exactly what happened here.

The founder in that screenshot didn’t just fail—he failed hard. He didn’t validate the AI’s output. He didn’t consider network security. He didn’t define architectural constraints, performance expectations, or abuse vectors. He didn’t even try to wrap guardrails around core features. He just handed the AI a vague prompt and got exactly what he asked for: something that looked like an app… until it got real users.

This isn’t a story about AI failing. It’s a story about someone skipping the entire engineering process and assuming the AI would just fill in the blanks.

It won’t. That’s not what it’s for. When you prompt an LLM, it's built to give you a response based on the tokens you just provided it. Sure, it's been pre-trained on a lot of other knowledge, but it's still designed to give you a response within its character limits based on the context you just provided it. That engineer didn't ask for a secure app, he didn't ask for a scalable app, he didn't ask for a maintainable app. He just asked for an app and an app is exactly what he got.

## You Still Have to Do the Thinking

I use LLMs all the time, but not to make decisions for me. If I’m not sure about an approach, I’ll use the advanced voice mode in ChatGPT and talk it out. It’s an incredibly useful sounding board. Explaining an idea out loud—even to an AI—helps me solidify the structure and catch holes in the logic before I even write code. It’s like pair programming with a seasoned engineer, except it never gets tired and always has a suggestion.

But I’m still the one planning the architecture. I’m the one defining the workflows. I’m the one deciding where the security boundaries go, how APIs should behave under load, and what edge cases matter.

If you’re not doing that upfront work—if you’re not engineering the solution—you’re not vibe coding. You’re just gambling with a boilerplate. And this is what I think is the biggest misconception about vibe coding; it's not about fully taking a backseat. If it was, I wouldn't still have a job; no software engineer would. 

## Real Vibe Coding Happens *After* the Plan

When I vibe code, it’s never at the start of the process. I’m not telling an LLM to “build my startup.” I’m using it after I’ve already mapped out the module I want. I might sketch the system architecture by hand, break it into individual components, and then call on the LLM to scaffold those components faster. I might say, “Here’s the schema, here’s the expected input/output, here’s the performance constraint—go build me the first draft.”

That first draft still goes through my review. I clean up what needs cleaning up. I expand on what needs depth. But vibe coding gets me out of the weeds faster and lets me spend more time on the parts that matter—business logic, performance tuning, and integration.

I’ve used this approach to generate:
- dashboard UIs once the data models were already locked
- backend logic for non-critical admin tools
- parts of internal modules where I’d already outlined behavior

But let’s be clear: most of my crypto suite *is not* built this way. My trading bot wasn’t LLM-coded. My infra orchestration wasn’t vibe coded. Most of my critical path is still handwritten, designed, and validated by me. I use AI to assist me when I get stuck or want to speed something up—not to do my job for me. There are a few modules that were fully vibe coded, but they are small parts of a larger system and were done to get myself to more interesting features faster.

## Vibe Coding Is a Multiplier, Not a Replacement

Used the right way, LLMs are an absolute productivity multiplier. They turn thought into action faster. But that only works if you *think first*. If you give it a loose idea, you’ll get loose results. If you feed it a system-level spec, you’ll get working components. Give it garbage, get garbage. Give it gold, get treasure.

That’s the core of vibe coding: the vibe isn’t chaos—it’s clarity. It’s building with energy, with speed, *after* you’ve already done the hard work of planning.

So no, I’m not out here saying “AI will build your startup.” I’m saying you still have to show up as the architect. And if you do, AI will absolutely help you build faster than you ever could alone.


## Furthermore...

It’s easy to misunderstand what good prompting looks like when you’re vibe coding, especially with all the “build an app with one prompt” content floating around. So here’s a quick side-by-side of what good vs. bad vibe coding actually looks like:

### **Bad Vibe Coding (Don’t Do This)**

```text
Prompt 1: Build me a SaaS app with user authentication, subscriptions, and a dashboard.
```

Then maybe:

```text
Prompt 2: Add a Stripe integration.
```

This kind of prompting skips all the context the LLM needs to give you anything useful or secure. There’s no architecture, no constraint definition, no error handling, no consideration for abuse prevention, rate limits, logging, or network security. The result? Something that looks right… until people actually use it.

### **Good Vibe Coding (Step-by-Step, Context-Rich Prompts)**

```text
Prompt 1: I want to build a web app for journaling moods. Users should be able to log in, add daily entries, and view trends over time. Let's start with the data model. Suggest a schema for PostgreSQL.
```

```text
Prompt 2: Great. Now generate SQL for the schema you just described.
```

```text
Prompt 3: I want the backend in FastAPI. Start with a skeleton that supports user auth and journaling routes.
```

```text
Prompt 4: Now add JWT-based auth for login and session management.
```

```text
Prompt 5: Create CRUD endpoints for journal entries, scoped to the logged-in user.
```

```text
Prompt 6: Add basic input validation and error handling for the entry form.
```

```text
Prompt 7: Now scaffold a simple React dashboard that fetches and displays entries from the backend.
```

```text
Prompt 8: Add a line chart that shows mood trends over time based on the fetched data.
```

Each step builds on the last. The LLM gets structure, constraints, and purpose. You're not just asking for an app—you’re *collaborating* to build something intentional. That’s real vibe coding.