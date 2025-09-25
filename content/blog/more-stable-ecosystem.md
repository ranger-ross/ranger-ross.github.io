+++
title = "A more stable Rust Ecosystem"
date = "2025-09-23"
description = "Thoughts on the state of the crates ecosystem"
+++

Rust is often praised for its ecosystem of packages (aka crates).
While [crates.io](https://crates.io) and its ecosystem of crates is indeed a big feather in Rust's cap, there has been a lingering issue with the wider ecosystem that has been irking me for sometime.
This being the hesitancy by the community to publish 1.0 versions for crates.
This post is my attempt to articulate my thoughts on this trend and why I think its holding back Rust.

The Rust community is quite disciplined in following [SemVer](https://semver.org/) and avoiding breaking changes, at least compared to other languages. [^1]
It's generally considered best practice to avoid breaking changes when making updates to a package.
This is because when you make a breaking change in a popular crate, it causes a lot of churn downstream.
Users need to read and comprehend the changes and modify their code requiring them to invest time in the upgrade.
Frequent breaking changes cause a lot of pain for users!

Since crate authors feel pressure to avoid breaking changes, they will avoid publishing a `1.0.0` of their crates.
In SemVer versions prior to `1.0.0` consider MINOR changes as breaking changes.
This means that going from `0.1.0` to `0.2.0` is a breaking change. [^2]
Once a crate publishes a `1.0.0` its considered "stable" signifying breaking changes are expected less often.

When Rust was early on many core crates were `0.x.x` to indicate to users that they were still trying to flesh out their APIs and experimenting with functionality.
Crate authors did not want to commit to the current API and leave room for future changes.
This was fine in 2015-2020, however fast forward to 2025 and we are in a very different landscape.
We still have many core crates that have not stabilized.

## The case for stabilizing

If you are a crate author, I want to make the case for you to consider pushing for a `1.0.0` release.

### Eventually what you got is what you got

The most common argument to keeping a crate `0.x.x` is the author not wanting to "lock themselves into an API."
This is understandable and reasonable when your crate is early on, but at some point your crate is what it is.
I have seen many crates, that have no active feature development but the author is still hesitant to publish a `1.0.0`.
Your crate will never be perfect. If your crate is multiple years old, you should seriously consider publishing a `1.0.0`.
It would be a better service to your users to stabilize your crate and consider a `2.0.0` if you really want to change the API in the future.

### Your crate is not the standard library

I believe one of the reasons crate authors are hesitant to publish a `1.0.0` is because they see the backwards compatibly promises from the Rust Project (official tooling like Rustc, libstd, Cargo, etc) and feel pressure to have similar guarantees.
While a noble aspiration, it's unreasonable for every crate to have such stability guarantees.
While Rust `2.0.0` is not planned, that should not prevent your crate from making a `2.0.0` release.

### Unblocking your dependents from stabilizing

Another good reason to consider stabilizing your crate is if your crate is a dependency for other crates.
When low level crates are `0.x.x`, it prevents high level crates that depend on the low level crate from stabilizing.
This has a compounding effect when their are multiple layers of dependencies.

If some key crates hit `1.0.0` it would allow entire ecosystems of crates to stabilize.

### Tooling

Many tools leverage the SemVer semantics for functionality including `cargo update`.
These tools are less effective when crates are `0.x.x`.
This is because MINOR changes are considered breaking changes so `cargo update` cannot safely update MINOR versions prior to `1.0.0`.
Once a crate is `1.x.x` `cargo update` can update to the latest MINOR version allowing users to get new features of a crate much easier.

### The social component

Even if your crate has been around for a long time and is reliable, being `0.x.x` gives the impression that its still alpha software.
I believe having so many `0.x.x` core crates gives people outside the community the impression that it's not ready for production deployments.
Often enterprises have policies preventing `0.x.x` packages from being used in production.
Sometimes these policies lead teams to use another language for their problem when Rust might have been an optimal choice.
Whether you agree or disagree these kinds of policies, they exist and likely aren't going anywhere.


## Wrapping up

I hope that the arguments above at least make some crate authors consider stabilizing their crates.
If you are still on the fence, I'd implore you to at least start a discussion in your issue tracker and consider a roadmap to `1.0.0` for your crate.
I want to point out that there are some crates like `serde` that reached `1.0.0` fairly early on and I believe the Rust ecosystem is better because of that. We have also seen many other crates like `thiserror` and `derive_more` hit `1.0.0` recently which is very important for the long term health of the ecosystem.


[^1]: So much so that a tool [cargo-semver-checks](https://crates.io/crates/cargo-semver-checks) has been created simply to make not publishing breaking changes by mistake
[^2]: This behavior is convenient when you are early on in development of a crate and rapid breaking changes are common.

