---
title: In Defense of the Spaghetti Code
date: 2021-08-01
image:
  path: https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Flv2cd3dep7806fxyfwad.jpg
canonical_url: https://dev.to/gervg/in-defense-of-the-spaghetti-code-1oha
categories: [SoftwareDev]
tags: [code-quality]
---


Anyone working in software would have probably seen a piece of code they wish was never written. Or at least was not written like it was meant to summon creatures from the underworld.

Funny enough that this tangled ball of mess is so common that we gave it a name: *spaghetti code.* And there are probably hundreds of articles, books, and memes about it - yes, we all love to hate it. Dealing with bad unmaintainable code is never fun. No one likes to touch a program that feels like a disaster waiting to happen.

So why defend it then?

Well folks, spaghetti code is still *spaghetti*.

![girl-eating-pasta](https://media.giphy.com/media/11uoNyauChZR16/giphy.gif)

## Everybody Cooks Pasta

When I started my career as a junior software engineer, I was surprised to learn about the rate at which our code changes. Before that, I've only worked with school assignments and projects. Once I've written it and it works, that's final. That's the *product* of my work. 

The real world isn't as nice though. Requirements will always change yet the product is expected to adapt as quickly possible. It is interesting that we, as an industry, has created subject areas, or a disciplines if you will, about making changes to software again and again - agile, refactoring, CI/CD, and a slew of other jargons. I don't know much about civil works, but it's probably crazy to think if they do have something similar to how we do software. Can you imagine bridges getting restructured on a daily or weekly basis?

But that's just the nature of software - nothing is ever permanent. Unlike a bridge, it is *soft* in a way that you can mold it in any way you want. It can change and be shaped to fit the ever changing requirements. You know, kinda like a dough.

![pasta-dough](https://assets.bonappetit.com/photos/57d828806520aa8f7013c947/1:1/w_2560%2Cc_limit/fresh-pasta-dough.jpg)

But what starts as a simple chunk of dough soon becomes pasta noodles. Cook it, add some sauce, meat, basil on top and voila!

I'm pretty convinced that spaghetti code (or its variants) exist everywhere, *c'est la vie.* That wouldn't stop me from checking  `git blame` , but I at least have grown to understand that most are just accidental chefs.

## A little empathy to the Accidental Chef

I don't think that anyone have intended to write code that looks and feels cursed from the get go. Maybe at the time that was the best way the authors knew how to implement it. Maybe their technical and/or domain knowledge is not ripe enough. Maybe they have limited resources and it was their conscious decision to cut corners. Maybe, maybe...

My point really is that software projects don't always go our way. We have to accept that it will grow over time and we have to weed out things that we don't like.

And the spaghetti authors? I'm not gonna jump my gun and call them incompetent or evil. I am pretty sure that I unknowingly have been in their shoes, and those who have to work with my code written months/years ago are probably cursing me right now.

## It's edible (and can be delicious)

So is it okay to write spaghetti code? No, it is not but mistakes are always bound to happen and this is one of the few things I'd treat as *excusable* and *remediable* (easier said than done, I know).

At the end of the day, we write code to create solutions. That spaghetti legacy code may be shitty as it can be. But if it works, provides value for the users, and generates income for you then it's still great.

"We can write clean code and still provide value to our users", you'll probably say. Then that's even better! Good for you. And that should be everyone's goal. Clean code improves developer experience and can improve turnaround time. But the reality is that not everyone may be capable of reaching that ideal state right away.

So I'd rather take baby steps with a little bowl of pasta than rush, trip over, and plant my face to a cake.

---

# Credits

- Cover photo by [Dario](https://unsplash.com/@dariox) at [Unsplash](https://unsplash.com/photos/TtadVut4jsg)
  Erratum (2025-06-01): Link seems broken
- Pasta Dough. Image by Alex Lau via [Bonappetit](https://www.bonappetit.com/recipe/fresh-pasta-dough)
