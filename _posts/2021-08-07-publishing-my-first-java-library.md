---
title: My Experiences in Writing and Publishing My First Java Library
date: 2021-08-07
categories: [SoftwareDev]
tags: [java, functional-programming]
---

More than a year ago, a friend introduced me to the concept of [Railway-Oriented Programming](https://fsharpforfunandprofit.com/rop/) (ROP). I liked the idea and the [fluency](https://martinfowler.com/bliki/FluentInterface.html) that comes with it, but it was a style born out of functional programming - something that is not fully embraced in Java despite the introduction of [lambdas and streams in Java  8](https://www.marcobehler.com/guides/a-guide-to-java-versions-and-features#_java_features_8_16).

Though there were already a few existing Java libraries for this, I thought it might be a good idea to write one myself as it was a good opportunity for me to:

- understand what ROP is
- practice TDD
- learn how to publish a Java library to a publicly available package repository (i.e. Sonatype Nexus)
- try to use GitHub actions to setup a pipeline and automatically publish the library to the package repository

![many-months-later-meme](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/29xg9or0flxhj7a7v8fh.png)

After a couple of months and tons of procrastination, I was able to came up with something usable albeit not production-ready (that wasn't the goal anyway).

> [**GervG**](https://github.com/Gerv-G) / [**jrail**](https://github.com/Gerv-G/jrail)
> - Railway-oriented Programming with Java
{: .prompt-info}

If you're curious, you can get the snapshot [here](https://oss.sonatype.org/#nexus-search;quick~io.github.gerv-g).

I'm planning to do a write up on what JRail is, what it can do and what I think are its shortcomings (though I think what I've made is not a true ROP). But that's not what this post is all about. For now, here are some thoughts and highlights from the journey:

## Naming is (still) hard

As clichéd as it may be but naming is really hard. I've been mulling over the name for almost a week before I settled for *JRail,* since most Java things either starts or ends with "J". It was only after the creation of the repository that I realized it looks like a name for Japan Rail. But hey, it has already been created and I don't wanna spend another week thinking for a name.

## I suck at GitHub

Prior to this, I don't have any serious repositories in my Github account. Most of what I have were more like scratch paper scribbles rather than showcase-worthy projects. So yeah, that's a pretty lengthy way to say I don't code outside of work.

![my-almost-empty-calendar](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yvvwwal5fwk83sofg77z.png)

Look at that contribution calendar. So impressive /s

It also took me an embarrassing amount of time to setup my SSH keys and the repository which should have only taken a few minutes if not seconds. This is a nice refresher, I guess.

## I don't think I truly understood Monads

And at this point, I don't think anyone does.

Kidding aside, I really wanted to understand the underlying theory in this. I believe it's perilous to simply do something without understanding why it is done in such a way. I remember consuming a lot of materials about category theory and functional programming when I first ventured into this project, but wasn't able to retain much information (my brain isn't great).

The closest I got to understanding it is with [this explanation](https://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html).

So I tried explaining it my own words to a friend, because "the best way to learn is to teach", right? But I couldn't answer his questions, so perhaps I really didn't get monads after all.

Like a normal person, I gave up. I may come back to it later if I ever had the motivation again but for now I think I've learned enough to proceed. I then shifted my focus on how I can make the API intuitive enough to use, of course with the help of tests.

## Spock is great but it didn't fit my needs

You've probably heard of the testing framework called [Spock](https://spockframework.org/), which is written in [Groovy](https://groovy-lang.org/). It's great and I love using it everyday for work. So I initially wrote all my tests using it.

But I realized that having a dynamically-typed language doesn't help me that much in designing the APIs (the not-so-strict Java generics isn't helping either). I also wanted to know what it's like to use the APIs I've made. So to avoid shooting myself on the foot, I decided to rewrite the tests with JUnit instead.

Another reason is that I wanted to let my tests serve as a documentation or a compilation of examples. I wrote this library with Java devs in mind, and having tests in Groovy is sort of a step towards a different direction. One of the few differences is Groovy closures where the syntax for lambda expressions uses curly braces instead of parentheses.

```groovy
{ closureParameters ->  statements }
```

While that may not be so significant for an experienced dev, I didn't want to add any additional cognitive load to the readers anymore. Writing the tests in Java made the "examples" clearer and consistent.

## Open-source Licensing Options

Why the heck are there too many of them? Thankfully, GitHub created [https://choosealicense.com/](https://choosealicense.com/) to help noobs like me pick the proper license.

It's unlikely that people are gonna use this anyway. But just in case, I wanted to let them know that I don't care what they want to do with it and I'm not liable whatever chaos they caused.

## Dipping my toes on GitHub Actions

It's my first time to setup my own CI and it was actually easier than it is to type this whole blog post. GitHub has already provided some workflow templates to get you started so it really is just a matter of clicking. It's also fairly easy to play around with since it's just YAML (as most DevOps things are).

## Creating and approving my own PR

I don't think I need to explain this. This is the best part of this project

![self-approve](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/a7gmfodeyacvhuui1o5e.png)

## Publishing the library

This is the most exciting yet frustrating part of the project. I was only able to [publish a snapshot](https://oss.sonatype.org/#nexus-search;quick~io.github.gerv-g), but I couldn't sign it properly. After multiple failures in my CI, I decided to skip the signing and just publish a snapshot. I didn't want to publish an unsigned package but I was too lazy to continue. I felt like I've already done what I ought to do so this is already enough of an achievement for me.

Yup, I'm lazy. I know.

---

## Final Thoughts
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fm8tm1ophxnvcknw5a32.jpg)

Building JRail was a pretty fun exercise despite my failure to complete it. I may comeback to it later to improve it and to revisit its paradigm since I don't think I've followed ROP. But realistically speaking, I'll probably just leave it as it is because I usually prefer to stay away from coding after work hours. It's just my own way of balancing things and taking the time to enjoy some other stuff.

Nonetheless, it's still a nice reminder for myself to always practice the basics and to sometimes explore what else I can do other than those that I learn on the job. I think I'll borrow some principles in ROP and apply them to our code.

## Relevant Articles

In case you're interested and wanted to try it or do some reading on your own, here are some of resources to get you started:

- [Railway-oriented Programming](https://fsharpforfunandprofit.com/rop/) by Scott Wlaschin.
This is the original source of the idea as far as I know.
- [How to Publish Open Source Java Libraries to Maven Central](https://entzik.medium.com/how-to-publish-open-source-java-libraries-to-maven-central-70f9232462f5) by Emil Kirschner.
I read other guides too but his is the easiest to follow despite it being written in Kotlin
- [GPG Cheat Sheet](https://irtfweb.ifa.hawaii.edu/~lockhart/gpg/)
- A bunch of functional-programming articles
    - [Functors, Applicatives, And Monads In Pictures](https://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html) by Adit Bhargava
    - [Your easy guide to Monads, Applicatives, & Functors](https://medium.com/@lettier/your-easy-guide-to-monads-applicatives-functors-862048d61610)
    This really looks cool with its animations
    - [This answer in Stackoverflow](https://stackoverflow.com/a/194207)
- [Category Theory for Programmers](https://github.com/hmemcpy/milewski-ctfp-pdf/) by Bartosz Milewski.
I haven't finished reading this book but it's really interesting especially if you're interested in the abstract topics of math
