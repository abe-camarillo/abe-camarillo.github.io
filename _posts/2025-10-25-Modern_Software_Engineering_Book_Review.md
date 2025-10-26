---
layout: post
title:  "Modern Software Engineering by Dave Farley | Book Review"
date:   2025-10-25 12:47:26 -0600
categories: jekyll update
---

## My recent experience developing software

I recently finished reading Modern Software Engineering by Dave Farley, and it's been such a change of paradigm for me. This year I have read several good books, but this one really impacted the way I approached code. I was initially looking for a book about managing software projects, because I identified the necesity of improving the way we developed software.

The approach I have been using in my workplace often seems slow, it takes some time to begin (because we want to define all the work at the start), and once we came up with an implementation at the end of the quarter, we identify the deliviered solution was distant of what we had in mind, and what is actually useful. I was hopeful too, that by reading some resources, we would be able to make better estimates on delivery dates, so we could avoid the embarrassment of having to pospone the release date.

## Redefining our task as Software Engineers

After passing through some content summaries and introductions, I casually ended up finding this book. Which more than just prescribing a way to estimate times of a given project, attempts to redefine how we think about software development or "coding", and as a byproduct explains how we can deliver valuable software faster. As a summary, Farley goes on in this book detailing what he considers to be "engineering of good software", by listing a small set of characteristics that makes software easy to change, and efficient to maintain. How we should move away of the mindset of "Production of Software", as if it was something that you can produce in a manufacturing line, and also to evolve from the idea of crafting software to properly engineer it.

He then explains how using a proper engineering aproach yields good quality software, by using a systematic approach that allows us to learn through iterative and incremental changes. Most of the chapters insist on those characteristics, how Dave defines them, and how we can evaluate if our code has these attributes. In a nutshell, Test Driven Development and Continuous Delivery are the means to achieve high quality software, and Dave explains in detail how this is achieved.

## How to Engineer good software?

For Dave Farley, the approach to produce good software, is to facilitate the means to engineer it. The goal characteristics of this kind of software are:

- Modularity
- High degree of cohesion
- Well separated concerns
- Well abstracted (hides it's implementation well)
- Loosely coupled

In that sense, finding a way to facilitate the software we make accomplishes those characteristics, is the way to produce valuable software fast. To do this, using Test Driven Development as a tool to achieve those characteristics is the key. In some way, placing the code in a test helps us to improve it's design by making it easier to test. Also, we abstract well the details of it's implementation, because we use abstraction in defining the test.

## Deploy fast and often

Another of the critical changes to the way we usually work, is to make our software easily deployable and fast to deploy. In that way, we enable ourselves to make small changes and learn from the user interactions with it. Once we learn more, we can add another increment and release it, making complex software.

## My personal oipinion

I've heard often that Test Driven Development is often difficult to achieve, or it only works in practice because you don't know the details before writing your tests. Personally I think this is a matter of discipline, because it requires to think carefully what you want and how to write the test properly.

Also, there are some things that are just plain difficult to place in a test framework. But in some way that should not stop us to add as much testing as we can. Because even if we don't do TDD in the strict sense, by testing we are still improving the design of the work we do.

## Conclusions

Most of the practices Dave describe in his book were already implemented in my workplace, like using deploy pipelines that enable Continuous Integration and Continuous Deployment of our software, but even when we have this tools, we need to shift our way of thinking to take advantage of them. By having our code in a releasable state using TDD and and learning through usage, we can achieve better designed software that will enable us to deliver value faster.
