---
layout: post
title: "four winds that shape the land"
date: 2025-08-08
author: "citizenhicks"
tags: ["ai agents", "langgraph", "llm", "ai engineering"]
---

The year 2025 is the year of agents, or so they say. Frankly, it looks
like we are on the path to figuring out how to build agents in production and
make them genuinely useful. From Claude Code to Deep Research, we have experimented with
numerous ways to make large language models practical. On this journey, we learned
that AI agents need to spend more tokens to be useful, which is now viable via
optimized inference and scaling of context windows. The industry has also identified
the four winds that shape the landscape of how we develop and build agents. These
four winds are: planning capabilities, depth of the agent architecture,
better (longer) prompts, and the terminal (marking the second golden age of terminals).
Let's break them down one by one.

## Planning Capabilities

Complex tasks require upfront thinking, even for humans. The industry started
to overcome this hurdle by introducing reasoning models, which helped significantly
(more tokens → better results), but something was still missing. Even with our best
[techniques](https://x.com/Teknium1/status/1951228980377588019) to date, we are only able to do so much to increase the context with reasonable callbacks.

This is where planning tools come to the rescue. Just like for humans, planning tools serve as scratch pads for AI agents, ensuring they have a clear plan of attack. Most importantly, they help agents maintain focus on the original task, goal, and the path to achieve them. Planning prevents the common pitfall of agents getting lost in complex multi-step operations or forgetting intermediate results.

Claude Code introduced and refined this technique brilliantly, and now many applications are adopting it. The planning phase typically involves breaking down complex requests into manageable subtasks, establishing dependencies between them, and maintaining a clear execution order. With LangGraph, it's relatively easy and natural to implement such tools using the graph state, allowing developers to create sophisticated planning mechanisms that can adapt as tasks progress.

## Depth of the Agent Architecture

For a long time, we used a single LLM to perform all tasks. Now we know that this
is not the optimal approach. Anthropic recently
[shared](https://www.anthropic.com/engineering/multi-agent-research-system)
their way of organizing the Deep Research agent and the reasoning behind
their architectural choices. It's actually quite simple and ties back to what we've been discussing:

> Multi-agent systems work mainly because they help spend enough tokens to solve
> the problem.

There you have it. Tokens are everything in this game, but not all tokens count equally.
When it comes to staying on track and not losing sight of the main goal, sub-agents
come to the rescue. They offload the token burden from the main agent while ensuring
we've exhausted all possible avenues to solve each sub-task at hand.

The beauty of this approach lies in specialization. Each sub-agent can be optimized for specific types of tasks—one might excel at code generation, another at research and information gathering, and yet another at synthesis and summarization. This division of labor mirrors how human teams operate, with each member bringing their expertise to bear on different aspects of a complex problem. The orchestrator agent maintains the big picture while delegating detailed work to specialized sub-agents, creating a more efficient and effective system overall.

## Better (Longer) Prompts

So far I've been discussing context length and reasoning and how these helped
realize the potential of agentic systems, but there are additional
underlying architectural breakthroughs. One is structured output, the other
is instruction-following capabilities. These become crucial when we get
to better (and longer) prompts.

Since we now have the capacity, we've been writing increasingly detailed
prompts in production—not just for agents, but also for tools and for
handoff calls between agents. These prompts are long and meticulously crafted. As
of the date of this post, most production prompts are now longer than the
original context window of ChatGPT, which was only 1,024 tokens! Meanwhile,
GPT-5 is now featuring [at least
256k](https://openai.com/index/introducing-gpt-5-for-developers/) tokens.

Longer prompts enable us to include comprehensive instructions, edge case handling, and detailed examples that help agents perform tasks to production standards. We're essentially encoding entire workflows, best practices, and domain expertise directly into prompts. This shift represents a fundamental change in how we think about programming AI systems—from brief commands to detailed specifications that can span pages of text, complete with context, constraints, and contingency planning.

## The Terminal

With the arrival of CLI coding agents, we have entered the second golden age
of terminal usage. To be fair, this should have come much earlier—LLMs are
fundamentally good at text generation, and terminals are text-based interfaces to control
computers and interact with systems. The match seems obvious in hindsight.

We've experimented with human-style control for LLMs through GUI automation and computer use, but I don't think this is the most optimal way for LLMs to control systems. Text-based interfaces provide precise, deterministic control without the ambiguity of visual interpretation. Every command has clear syntax, every output is structured text, and the entire interaction history can be easily logged and debugged.

Looking forward, I believe every major service will eventually introduce Model Context
Protocol (MCP) based access to their APIs, creating a standardized way for AI agents to interact with external systems. The terminal-based agents will likely outlive the operators and computer use agents because they align better with the fundamental nature of LLMs. The terminal renaissance we're witnessing isn't just nostalgia—it's a recognition that sometimes the old interfaces are the most powerful when paired with new intelligence. Time will tell, but the command line's simplicity and power seem perfectly suited for the age of AI agents.

thanks for reading.
_find me on [X/Twitter](https://x.com/citizenhicks) or [GitHub](https://github.com/citizenhicks) for more discussions about ai and software engineering._
