+++
title = "The Evolution of Rust"
date = "2025-05-03"
description = "Thoughts on how Rust is evolving"
+++


I started learning [Rust](https://www.rust-lang.org/) in late 2022 after finally giving into the hype.
Two and a half years later I now completely understand why there is so much buzz around this language.
It solves so many of the pain points I have had in other languages and I generally just find writing Rust more engaging.

However, Rust is not all sunshine and rainbows. There are real pain points that need to be addressed if Rust wants to compete with other popular programming languages.
Many of these pain points are well known (slow compile times, steep learning curve relative to other languages, etc) and I do not have much to add.
But I do want to explore a topic that is less talked about but is very important in my mind. 

**Rust's selection of new features and managing the complexity of the language**

Rust has been changing rapidly over the past 10 years and this has helped fuel it's success.
After 10 years since 1.0, Rust has a gained a lot of features.
I have began to wonder if the pace of new feature additions is healthy long term.
It begs the question "What will Rust look like in 2035?"

To be clear, we need new Rust language features as we do not want the to stagnate.
But at what point is a langauge solidified and the pace of which large langauge features added slowed down?
I am not saying Rust is at that point yet but its an interesting question to ponder.

## Onboarding Friction

Rust has a reputation for being difficult to learn/use compared to "higher" level languages like Javascript and GoLang.
I feel this is a bit overblown, especially for modern Rust. Personally I find that I am nearly as fast if not faster in coding in Rust as I am in other languages.
However, I did find the learning experience quite difficult compared to other languages.

Rust has a lot going on. It has a lot of features that you need to interact with in even simple programs.
When learning Rust, one of the pain points I felt was the sheer amount of new concepts I had to learn to get up and running.
While many of the features in Rust are worth while and improve the development experience they increase the learning curve of the language.

As someone who has introduced Rust at their workplace and is viewed as the "Rust expert" [^1], I spend a lot of time teaching Rust and helping teams migrate to Rust.
A good amount of effort for teams onboarding is getting up to speed with all of the features in Rust.


## New Syntax

At this point in Rust's life, new features should have pass high bar of scrutiny to be accepted.
This is especially true for features that introduce new syntax.
We already have a lot of syntax in Rust relative to other languages. 
Adding new syntax is a tradeoff between making things easier to write (and sometimes read) while requiring users to be aware of this semantics behind the syntax.

Every time we add a new keyword it adds more things for the user to be familiar with to understand what a program does.
The Rust type system gives the user many ways to express their problem, which is great but comes with the drawback of increasing burden to understand code that you did not write.
I sometimes feel this in code reviews when the author uses a syntax that I do not commonly use.

To point to a specific example where I think this is applicable is [RFC 3680](https://github.com/rust-lang/rfcs/pull/3680).
To summarize the RFC (as currently written on May 3, 2025), It proposes that we reuse the `use` in a few new ways to make working with `Arc`/`Rc` a more ergonomic.
As currently written, I do not think this RFC provides enough benefits to outweigh the downsides of introducing new syntax to the language. 
There are many comments on this RFC that echo similar sentiments.

My goal is not to pick on this RFC (as the goal is noble) but simply to illustrate that bar to introduce new syntax/keywords should be very high and needs to meaningfully solve existing problems.


## Refining Existing Features

One interesting data point in the [2024 State of Rust Survey](https://blog.rust-lang.org/2025/02/13/2024-State-Of-Rust-Survey-results/) was the results of "What is your opinion on how fast Rust evolves?"

![](/img/what-do-you-think-about-rust-evolution.svg)


With the options provided I would probably fall into the "I am satisfied with the current pace of development" bucket.
However, the current options miss the difference between introducing new features and improving existing features.[^2]

I find that I often desire improvements to existing Rust features rather than new features entirely.

A great example of this is the "Async Rust". Async Rust is not a new feature, but it still does not feel "complete". 
Async traits are still not dyn comptaible without using [async_trait](https://docs.rs/async-trait/latest/async_trait/), Async closures (this was stabilized in Rust 1.85), [Async Drop](https://rust-lang.github.io/async-fundamentals-initiative/roadmap/async_drop.html) is still unstable.
In 2025, I am the most excited about the [project goal](https://rust-lang.github.io/rust-project-goals/2025h1/async.html) to refine async rust.


## Tooling Features

Until now, I have been primarily talking about language features and not the greater Rust ecosystem.
I have a very difficult perspective on adding new features to tools in the Rust ecosystem.

Above I argue that introducing language features make the language more complex and introduces development friction when working in a team.
For tooling features, this usually does not apply. For example, `cargo build` hides a lot of the complexity of interacting with `rustc` and makes Rust development vastly more approachable.
Most tooling features reduce the complexity of Rust users need to deal with on a daily basis.

I hope to see the ecosystem of Rust tools continue to expand and mature in the coming years. [^3]

## Recap

1. Rust is already a relatively complex language. We need to be conservative when adding new features.
2. New language features need to meaningfully solve problems that real users have.
3. Refining existing features is not the same as introducing completely new features.
4. New tooling features do not increase the language complexity in the same way as new language features.

None of this is particularly ground breaking, but I think there is some value in having it written down as other may have opposing thoughts on how Rust should evolve.
I am largely optmistic on Rust's future but we as a community should be selective on which features we introduce into the language.

---

[^1]: I would not call myself a "Rust expert", but from my discussions with other in the community this is often how people that introduce Rust at their workplace are viewed.
[^2]: It's worth noting that this was [discussed](https://rust-lang.zulipchat.com/#narrow/channel/122651-general/topic/Selected.20results.20from.20the.20State.20of.20Rust.202024.20annual.20survey) in the Rust Zulip. And the survey will likely be tweaked to take this into account.
[^3]: While introducing Rust at my workplace, many of the pain points I ran into were trying to make the Rust tools play nice with our existing systems.

