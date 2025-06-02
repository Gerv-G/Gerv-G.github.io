---
title: Test-Driven Development isn't about Unit Tests
date: 2022-07-17
canonical_url: https://dev.to/gervg/test-driven-development-isnt-about-unit-tests-48e3
categories: [SoftwareDev]
tags: [tdd, unit-testing, software-engineering]
---

I've met quite a number of people excitedly talking about how they wanted to adopt TDD (test-driven development), citing its ability to “catch bugs before you make them” or something about improving the code quality. While that is not entirely wrong, I think it's a bit misguided and overlooks TDD’s foremost benefit.

Worse, some of them seemingly take TDD as if it's an interchangeable term with unit testing. I am not being pedantic - unit testing is an art of its own and you can write effective tests without doing TDD. Unit test's responsibility is to ensure that your code works as intended; TDD's job is to help you get your code working as intended. See the difference, no? Okay, let's first talk about unit tests.

## Everyone loves unit tests
Devs hate meetings. But what do devs love? Writing code, of course! So much so that we're also writing code to test code. The most common of which are unit tests.

![I heard you like code](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pbydg6bahqpfjxzbrn19.png)

Unit tests help us slice our programs into smaller individual pieces (units) and test them independently. They're cheaper to write (relative to integration/end-to-end testing) and they provide very quick feedback to the developer. With just a quick run on the CLI or IDE, a dev can easily find out if something broke. Unit tests are your first line of defence against defects. Martin Fowler describes how it serves as the foundation of your [testing pyramid](https://martinfowler.com/bliki/TestPyramid.html).

When you write unit tests, your objective is to _test_ and ensure that your production code works as expected. Now let's move to TDD…

## Driven by Tests
There are A LOT of other *X-driven Development*: BDD, DDD, FDD, etc.

I'm starting to think the industry sometimes just loves to formalize processes and slap them with _-driven development_ on its name. Kidding aside, let's take our focus back on TDD.

I believe there's a subtle problem with the name “test-driven”. Not that I think I can do a better job than Kent Beck, but it seems that the name led people to conflate testing with TDD.

But the operative word here is “driven”. TDD is a development technique driven by tests. **Tests are the means not the goal**. The goal is still to write functioning production code and you're just leveraging the power of tests while doing so.

### F*ck around and Find out
Have you seen this meme?

![Scientific method is f*ck around and find out](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fp3r87y3t5p7k1lelmvv.png)

It's a funny, perhaps oversimplified, overview of the scientific method. But I think it's a very good analogy to what TDD is meant for in software development.

Writing unit tests in TDD is similar to coming up with a hypothesis and preparing the workbench in a lab. You have an idea in your head, and you verify it with an experiment. Oh, the idea didn't work - tweak some variables and run the test again. Did it work this time? See if it can still be improved… the cycle repeats. [Red-Green-Refactor](https://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html) is exactly that!

TDD is for times when you don't have a clear path ahead yet. It's for discovering the solution and refinement. It is a [design activity](https://www.developerdotstar.com/mag/articles/reeves_design_main.html). Take for example, a method signature. When writing tests, you think about the signature first but not yet the implementation details. How do you want it to look like? Inputs? Outputs? Is it easy to wield? And so forth.

**TDD is a technique meant to help you iteratively reach your objective: a working software**. So maybe, we can call it _experiment-driven_. But after a quick Google search, that name is already taken. Gosh darn, naming is indeed hard.

## Quality is a by-product
Let's talk about quality on two fronts: correctness and maintainability.

When you do TDD, you write tests (duh). These in turn cover a huge chunk of your code base. While code coverage is not necessarily indicative of good quality, the tests created through TDD gives some confidence that your production code works based on the assumptions you've established. These tests also create a safety net, guaranteeing that existing behaviours will not be accidentally changed when modifying the production code.

TDD also levels up maintainability by producing testable code. Sometimes when writing tests after production code, you might find yourself having to deal with a lot of coupling between different parts. This makes it hard to test them independently. TDD inverts that process hence you end up with code that is surely testable.

So yes, TDD helps improve quality. But **it is not the quality gate**, tests are, regardless if you write them before or after.
