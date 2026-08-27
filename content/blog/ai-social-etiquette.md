+++
title = "AI social etiquette"
date = "2026-08-27"
description = "Observations on when its okay and not okay to AI generate content"
+++

Lately I have been thinking a lot about when its socially acceptable to use AI generated content
when interacting with others. I am far from the only one to do so as there has been a lot of buzz around
various open source projects setting AI policies. (Rust, Zig, Java, Linux, etc)
Personally I have been grappling with this issue for a few months now and my opinion has been changing over time.
I have heard a lot of good arguments on both sides for different situations that I'd like to go into in this post.

As someone that is involved in open source software, I have paid loose attention to some of the AI policy discussions
going on in different communities. OSS communities often ban AI content in forum where another human is going to read it. (e.g. GitHub issues, PR descriptions, comments, etc) This does not represent all OSS projects, but I find that is the general direction many seem to be going in.
I also have a day job and have many coworkers that are enthusiastic about AI as a technology.
I honestly wish I was as excited as other about AI, but I am happy they are enjoying it.

For the last few months my thinking has been:

> If the primary purpose of the content is to be consumed by another human, you should not use AI.

This feels right to me. If I spent my time to write out a message to you, I feel its common courtesy to write your
thoughts in a reply without AI dumping a response. [^1] I say primarily because source code is meant to be consumed by humans, but I think at this point we can all agree that AI generated code _can_ be useful if done responsibly.
If you are generating some artifact that's primary purpose it not human consumption, it feels fine to be to use AI if it saves you time. I generally tried to divide up communication into two categories: "For humans" and "Not for humans" and use that as a basis of whether it was acceptable to use AI.

However, over the last few months my views on this have been challenged a couple of times.
Recently I've been have a pretty good back and forth with a coworker who sees AI social etiquette differently than me.
I will do my best to not misrepresent their argument, so to my understanding it effectively goes:

> Content should be judged on it's quality regardless of whether its AI generated or human generated.
> If the AI generated version is of the same quality level of what a human would produce, why does it matter
> how it is created?

And honestly, I didn't have a good response to this.
"Because we are humans and I don't want to talk to an AI" was the best that I could do at the time.
I think it'd be easy to just dismiss this and move on but I've been thinking about this conversation lately wondering if my previous framing is incomplete or just wrong.

Having sit on for a couple of weeks now I think perhaps my "for humans" - "not for humans" (FH/NFH) framework is too simplistic.
For example, how is it any different if I send someone a Slack message and they google the answer and send me the answer vs using AI to get to the answer? It's just a tool, right? I think the knee jerk reaction of many (including myself) would be to say that the AI is not capable of verifying the truth, and they'd be right with current technology.
But what about cases where they use AI as a shortcut but do something to verify the answer?
Is it okay then?
Do they need to change it or rewrite?
How much rewriting is needed?
Is this basically the new [ship of Theseus](https://en.wikipedia.org/wiki/Ship_of_Theseus)?

I've been stuck thinking about this for a while.

Today, there was an event at work which brought this topic back into my head.
Basically it was a case of a person creating JIRA tasks with heavy usage of AI which lead to confusion because the AI had generated a wall of text with subtle mistakes causing the person doing the task to struggle.
You could say that the person should not have used AI to create the tasks and I'd agree.
But what if we lived in a world where the AI was able to do this task perfectly. Would there be any harm in this?

In my opinion no.

It's less about communicating with on another person and more about organizing work.
This issue here was quality, the AI just didn't do a good enough job and if it had, I don't think anyone would have cared.

This is interesting to me because it goes against FH/NFH, yet I feel okay with it.
In a way the artifact itself feels like a middleman. I am communicating to some document and someone just happens to and read from it. So I feel like bad about using AI to generate since the purpose is not to have a human to human interaction. This is vastly different than something like a Slack conversation where conversation is more direct and substituting your own thoughts with AI feels wrong.

That said AI is cannot do these tasks to human level quality yet.
Conflict occurs when someone uses AI for these kinds of use cases with the assumption that it will be able to do this kind of work good enough soon so we might as well start using them early, but leads to other suffering.
While its very tempting, often using AI for these kinda of tasks ends up saving time for someone while taking it away from another.

Maybe another way to view the social etiquette for using AI is:

> Does this negatively affect someone else compared to if I would have otherwise created it by hand?

This framing does not capture the importance of human to human interaction, but is interesting nonetheless.
If I generate something to save my time, does it rob someone else of their time since they have to read it?
This makes the assumption that AI generated output is often overly verbose, which at the time of written is a well known and largely unsolved problem.
In the ideal world where AI content was concise as human content maybe this way of viewing it wouldn't make sense, but we live in the real world.
However if you take the time to clean up the AI's output such that it does not negatively impact other's maybe its fine.
The trouble with this of course, is that its really difficult to cleanup AI output so often attempts to do so are sub par.

For me, I think there is a middle ground between these ways of approaching it.
When communicating directly to another person you use your own words. Use AI as a tool and not a replacement.
When communicating to an artifact to be consumed by another person, its probably to use AI as long is using it would not negatively person on the other side.
My views on this are still evolving so maybe I will feel differently in a year or two as the technology changes, but I at least wanted to capture my thoughts on the current state of things in case they are useful for others.


[^1]: I recently came across [a website](https://noslopgrenade.com/) that illustrates this pretty well.



