+++
title = "AI and (Docker) containers aren't so different"
date = "2025-10-18"
description = "Comparing the impact of AI on the software development industry"
+++

Over the last few months I have been noticing a shift in the public perception of AI and how it will impact the software industry.
The utopic vision of AI automating all aspects of the development lifecycle is quickly eroding.
There are a wide variety of views on this and I of course have my own. But I have been struggling to come up with a way to articulate my thoughts on where I think the future of AI in software development is going until earlier this week.

I believe that AI will have a similar impact on the software industry as Docker and containers did in the 2010s.
I'd like to make the case that AI **will** have a large impact on software industry but not as some may believe.

## Why containers?

The idea of containers has been around for a long time but really took off in the mid-2010s with the introduction of Docker which adds nice ideas like images and layering. These concepts made working with containers much easier and the trend of using containers exploded. Fast forward to the 2020s and most modern systems are deployed using containers.

Containers changed the way we deploy and distribute our applications. Containers allowed you to deploy without the worry of if the server you deploy to had the correct dependencies installed. This portability was a game changer for complex applications, especially during the rise of cloud computing.
Containers also made it very easy to distribute applications and tools with others. It's fairly common to spin up a database using docker during development with a single `docker compose up` command.

My point here is that containers undoubtly changed the way we write and develop software.
My claim is that AI will have a similar level impact but in different ways.

## Agents and false dreams

For the past 2 years, there has been a huge push to operationalize AI agents.
The idea behind an agent is that is autonomous and does not require continual input from a human.
This frees up the human to do other more important work (or allows the companies replace them if you are cynical).

The deploy of agents have been mixed thus far. There are sparks of brilliance with a lot of mediocre results in between.
The fundamental issue that has emerged is AI is not reliable on non-trivial problems in real code base.
This is really bad for those that have the vision of replacing humans with agents because until they are reliable a human is needed to double check their work.
AI reliability is not likely to dramatically improve with a fundamental reachitecture.

The latest trend I have seen is the idea that a human operator will orchestrate many AI agents.
A small army of AI agents would process in parallel and the human would verify and course correct as needed.
Having the AI do segments of work in the background would theoretically still be a productity win even if limited to the review speed of a single human.
I think there is some reasonable application here but we are limited by the cognative load of the human operator.
I don't see a world where we are scale pass 3-5 agents per human on any non-trivial problems.
There are just too many code changes for a human to reasonably be able to keep in their head and think about the edge cases where the AI may be doing something wrong.

Agents may work in some limited areas but we are nowhere near a general purpose AI agent for for software development.

## A more realistic impact

AI is going to be a **tool** for engineers just like containers.
I believe the future is going to largely dominated by high focused AI tools that accompish a very specific task in the development lifecycle.
Similar to when containers were introduced, the overall approach we take to develop software will not change but the tools will.
I believe the true advantage of AI is to get small frequent wins that add up overtime instead of trying to have an AI do large higher level tasks.

In fact, I think a large amount of these tools are already available to us.

* GitHub Copilot (not the agent) provides a AI autocomplete. This is generally focused to a single function making the possible number of mistakes smaller and being low overhead of a human to review and iterate on.
* Using AI to review human created work (in fact I used ChatGPT to review this article)
* Using AI to orient yourself when working on a unfamiliar problem. Its great to get a rough overview a of problem space and learn some terminology so that you can refine your Google searches to find trust worthy sources.

The important thing to note is that the high level functions of software development are not going anywhere.
Software engineer, engineering management, project manager, and designer roles will still exist.
There will still need to be planning, development, testing, etc.
Each of these processes will likely change in some ways (hopefully for the better) but the overall software process will largely remain unchanged, just like when containers became popular in the 2010s.


