+++
title = "YakMan"
description = "Basic, storage agnostic config manager"
weight = 1
template = "page.html"
date = "2023-11-30"
repository_link = "https://github.com/ranger-ross/yakman"

[extra]
local_image = "img/yakman.png"
+++

# What and why

[YakMan](https://github.com/ranger-ross/nihongo-stats) is a config manager for applications. In modern software development its very common to need to abstract some configuration out of applications so that it can be quickly changed without rebuilding/deploying. 

There are already many solutions out there for managing config so why bother creating yet another?

Let me answer this with a short story...

### Why

I recently joined a new project and most of our configurations were either:
1. Hardcoded in the app
2. Stored in Kubernetes manifest files

Both of these required an application restart which at the time was slow and required a lot of red tape cutting to do.

I thought surely there was some open source solution that would make this easy. But after researching for a few days, I felt that there was not a solution that I really loved. 

This lead me to create YakMan.

### Goals

What I really wanted was a config manager that is:

1. Language agnostic
2. Support basic organziation/grouping featuers
3. Bring your own storage. No vendor lock in and does not require a specific cloud
4. Ability to hotswap config with application restarts
5. Modular with the ability to extend if desired 
6. Some basic access control
7. Free and open source


# Tech Stack

- Rust 
- Actix
- SvelteKit
- Tailwind

### Why this tech stack

I started with the "core" config manager API. One of my goals is a modular design and being able to swap the UI for your own custom UI is important to the project. For that reason, I decided to go with Rust+Actix for the backend service to create a REST API. Rust is nice for its amazing DX and great type system.

For the UI, I originally tried to use [Leptos](https://leptos.dev/) to keep everything in a single language (Rust). However, I ran into some challenges with Leptos:

1. Leptos at the time was very new (like a few month old) and this might it was still very rough around the edges.
2. Lots of lifetime issues and fighting the borrow checker constantly. 

I think that Leptos has an awesome community and a bright future. The Discord was always very helpful for newcomers and there are a lot of smart people in it.
But with being relatively new to Rust and Leptos being so young I had to make the hard decision to move to another frontend framework.

I did some researching and considered my options, and finally landed on SvelteKit. I wanted YakMan to feel lightweight and very snappy, so I was hoping to avoid many V-Dom like React and Angular. I landed on Svelte because offers a very nice DX and makes state management very simple.

And after a very large PR to replace Leptos with SvelteKit, I was left with the current tech stack for YakMan.


# Lessons Learned

### The adapter pattern is awesome

One of the goals for this project is to be able to "bring your own storage" meaning if you on AWS you can S3. If you are GCP you can use Cloud Storage. If you already have a MySQL database and want to use that sure. Just want to store the files locally on an EC2 server, I probably wont reccomened it but you can. One of YakMan's biggest features is being (somewhat) storage agnostic.

To implement feature I used the [adapter pattern](https://en.wikipedia.org/wiki/Adapter_pattern). I create a `StorageAdapter` trait in Rust (similar to an interface in our languages) that provided methods to read/write data to different storage services. This was probably my best decision I made during the early development of this project.

To add support for new storage service, I just needed to implement the `StorageAdapter` trait for that service and it would "just work." It was honestly amazing to see YakMan run bug free on a completely different database after just 30 minutes of coding to add a new adapter.

### OAuth and SSO can be tricky

OAuth 2 is a very complicated protocol. There are many different "flows" and it a be tricky to work with especially if the OAuth provider does not follow all of standards. 

When implementing Single Sign On for YakMan, I ran into a handful of issues where OAuth providers just did not implement some part of the OAuth protocol. This was frustrating but taking a step back I can understand why. OAuth has been a constant work in progress for over a decade now. It has been implemented many RFCs and there are many flows that serve different purposes. It is understandable that not all providers support every feature to the latest RFC.

This introduced some challenges and now I understand why many SaaS products charge for SSO. Its a lot of effort to maintain and very difficult to support all identity providers.
