---
layout: post
title: Understanding, as we understand it, is misunderstanding.
date: 2025-09-01
author: citizenhicks
tags:
  - ai
  - agents
  - langgraph
  - engineering
  - workflow
  - ai systems
---
We tend to believe that we understand the things around us, especially the things we create. Engineers are the creators of systems; they need to know that they understand what they have created and can predict the behavior of that system. With AI agents, this is not the case, even if a lot of people like to pretend otherwise. We have the endless stream of AI influencers on YouTube and Twitter who claim they have found the best way of working with AI agents. We have business leaders, especially consulting leaders, who pretend they have unlocked the hidden secrets of AI. Reality is sobering, but before we go into AI agents, we need to talk about LLMs, AI workflows, and then we can conclude on the current state of AI agents.

Since this is a very complicated topic, I will simplify my discussion around AI agents which are built with Large Language Models only. This will keep the topic relatable.

## LLMs

The bare-bone models (that is, base models) are not really useful for everyday people. These are not trained to talk to people or to follow instructions. In some ways these models are better, given that the negative side effects of instruction fine-tuning are not present. Therefore, base models are not the end product and rarely get released to the public. In order to make the model actually useful, we fine-tune them. The fine-tuning process is getting more and more complicated by the hour, but really that is the key to unlock the potential of the base model itself. Fine-tuned models are powering ChatGPT and Claude, and really the use of these is quite limited. You can talk to it, it can do search for you, maybe even write some code. The intention of these chat applications is mostly to please a wide public where the users and the use cases are quite diverse.

We also have models which are fine-tuned for other tasks. The most prominent ones are coder models; these are somewhere halfway between the LLMs as they were and the next step in evolution: AI agents.

We tend to believe we understand how LLMs work, but in reality nobody knows this still. There is a great amount of research going into understanding these models. One of my favorite tools to do that is Anthropic’s [circuit tracing tools](https://www.anthropic.com/research/open-source-circuit-tracing). This is really about understanding how the model gets to the answer it gives, and it is a step in the right direction, but there is a lot we don’t understand; still.

## AI Workflows

AI workflows, as I define them, are the bridge between a simple model with some primitive tools and a fully agentic system. This is just one step away from UiPath automation, like looking at my code which automates the Twitter account [PapersInML](https://x.com/papersinml), or anything you can build with [n8n](https://n8n.io/). You will need to define the steps the agent will take, and in some part of this workflow, the steps will be driven by a large language model. Let it summarize text (like email summary tools or PaperInML) or automate certain repetitive but well-defined workflows, such as giving access rights to people joining the Slack channel or Discord.

I think this is the most advertised field of current AI. The YouTube and Twitter tech bros, but even corporate guys and consultants, love to throw around the workflows they build and how it automates **everything** in their life. Well, we all know this is a lie, but let’s dive into why; this will give a strong foundation for the next and final topic.

There is a really good saying from [LazyProgrammer](https://lazyprogrammer.me/) that this field is not an engineering discipline; it is research at its heart. What this means is that we cannot really predict what works. You need to experiment with it.

I know it’s sad, but the reality is there is no one way of building a workflow which you can just go and copy-paste to your systems and hope it works. I am working with workflows and AI systems for a while now, and one thing I noted is that there are always some nuances to this, especially looking at edge cases which these workflows do not handle well. This, however, can be overcome with a good engineering mindset. You need to look at workflows as nothing but user-driven systems, accounting for the LLM as a user. That is, we need to account for all the little silly mistakes or misuse by the LLM so we don’t get funny results, such as this on Twitter: [“sorry, i cannot provide the response you are looking for”](https://x.com/search?q=sorry%2C%20i%20cannot%20provide%20the%20response%20you%20are%20looking%20for&src=typed_query&f=live).

So why you cannot **automate** your life? Well, for one, your life is more complicated and our world is built to interact with humans; not text based systems. 

Overall, I still think AI workflows are great. These are one notch better than UiPath/Alteryx workflows, and in my mind these are the most useful version of AI integration to date, if the engineer who is building and maintaining it actually knows what they’re doing. Still; I do not think you can automate **everything**  In my view, these types of systems are the best for corporate use to date, even if they’re not as **sexy** as the next topic: AI agents.

## AI Agents

This is a very exciting area of research at the moment, and admittedly the year 2025 is the year of AI agents. Some people distinguish between multi-agent systems and AI agents, but in my view the two are the same thing. Anthropic first [defined how to build an agentic system](https://www.anthropic.com/engineering/building-effective-agents), then also gave us a handy guide on how (and why!) to [build multi-agent systems](https://www.anthropic.com/engineering/multi-agent-research-system). I will not repeat the definitions and the best practices, but I want to focus on the fact that somehow every corporate and consulting leader is jumping on multi-agent systems directly without understanding what an AI agent is and why you need to go to multi-level. I will tell you upfront: most teams do not need multi-agent systems. In fact, you can do more harm than good. **Let’s see why.**

An AI agent is way more autonomous and more unpredictable than AI workflows. You essentially give a selection of tools and access to the agent and pray that it will do the right thing. Often it will not do the right thing and may even [delete your production database](https://x.com/aubetony/status/1941466629705171104). I have experienced this many times even with the best of agents (Claude Code), when the agent just decides to remove stuff because it is **hard to fix the code**. Truly an intern at its heart. All in all, agentic flows are still the best thing that ever happened in 2025 in the field of AI. One thing to keep in mind: **an agent can make a 0.5x engineer 0.001x, but an agent can also make a 2x engineer 10x.** After all, this is just a tool you use; the results are a reflection of your capabilities.

Multi-agents are hot right now. Very few teams I have seen can actually design a good multi-agent system. Twitter and YouTube went crazy when Claude Code allowed sub-agents, and they have immediately made their development workflow worse. [Look at this](https://x.com/Saboo_Shubham_/status/1961437531486204177). Let me be clear: you don’t need a lot of agents. The AI does not gain **specialized** knowledge or expertise by prompting it or because you named it an expert. That is not the reason to build multi-agent systems. Let me give you some of the real reasons you may want to create an agent which is specialized in nature. This list is based on Anthropic guidance and my own experience over the last 6 months building very complicated systems at first, just to keep deleting agents after realizing I have fallen for the hype:

1. **Context engineering:** AI has a context problem, especially in agentic use. Users will send messages and instructions; AI will read files; it will try to amend code which users may reject; it will search the internet. In reality, agentic use of AI burns a lot of tokens, some of it is useful to keep in context, some not. Like if you need to research the documentation of certain frameworks, outsource it to another **context** (sub-agent) and only keep the end result in context for the main agent.
2. **Very specific prompts:** You may want to perform certain standardized tasks with specific prompts. Such as, I have a release workflow for a FastAPI server (Python) but also for a Next.js server (TypeScript). These two have very specific steps to go through and fix the linting, update package lock, update the release YAML for the server config, etc. Almost like a workflow. This will also generate a lot of tokens. All the linting errors and builds will clog your main context (see item one) if you are not careful. For this, you can build a very specific step-by-step prompt for the agent which then executes this on its own.
3. **Async execution:** When you are confident enough about your system, you can try and experiance the hell of async execution. In theory, this can speed up the rather slow LLM token generation by going parallel. Good luck to you and to your lead agent keeping every sub-agent in line! Jokes aside; this is very powerful but does require a lot of experimentation. 
4. **You want a different model:** In some cases, you can use different models for tasks, such as researching on the internet to save money, to speed up with a smaller model; or to have a specialized fine-tuned version of some of your models. Claude 3.5 Haiku is famously good at summarizing text. I use it for the Twitter workflow; Claude Code uses it to summarize context.
5. **You just have too many tools:** When you build a general-purpose-ish system or even a specialized one, you can end up having 10+ tools for your main agent alone. Even GPT-5 gets confused with more than 10 tools. When this happens, one way of fixing this is to create sub-agents and allocate the tools to various agents. Now this will slow down the process and the sub-agents can have a lot of hit-and-miss, but if you do it right, you can gain massively from this. I don’t have a formula for you to try. You just need to go and try your ideas first, then try harder!

Well, these are my main reasons I think are valid to build a multi-agent system. You may have a different list, but with 400k context window and capable models, you quickly realize that you have very few cases when you need a multi-agent system.

Let me go back to the title: understanding, as we understand it, is a misunderstanding. I think you see why I say this. AI, AI workflows and AI agents have been understood, simplified, and explained by many, but in reality we don’t understand these as well as we like to claim. The above demonstrates that this tech can be very useful, but you need to follow your engineering process to make it work.**You must design your own systems from the first principle**. There is no shortcut to this. Do the corporate folks understand this? Probably not: [MIT Finds 95% Of GenAI Pilots Fail](https://www.forbes.com/sites/jasonsnyder/2025/08/26/mit-finds-95-of-genai-pilots-fail-because-companies-avoid-friction/). 

thanks for reading.  
_find me on [X/Twitter](https://x.com/citizenhicks) or [GitHub](https://github.com/citizenhicks) for more discussions about ai and software engineering._
