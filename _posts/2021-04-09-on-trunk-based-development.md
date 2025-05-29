---
title: On Trunk-based Development 
date: 2021-04-09
image:
  path: https://images.unsplash.com/photo-1502082553048-f009c37129b9?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
canonical_url: https://dev.to/gervg/on-trunk-based-development-3n10
categories: [SoftwareDev]
tags: [devops]
---

Observation and insights on our team's attempt at Trunk-based development

## Background

Earlier last year, our team was asked to switch from GitFlow to Trunk-based development. The change of course didn't happen without receiving opposition, complaints, and whatnots.  But it is worth noting that using GitFlow has its own fair share of pain points, which is likely the reason why our engineering leads decided to try Trunk-based development instead.

Trunk-based development was introduced to us using the [Microsoft's Release Flow](https://docs.microsoft.com/en-us/azure/devops/learn/devops-at-microsoft/release-flow#:~:text=The%20Release%20Flow%20model%20is,our%20developers%20can%20keep%20working.), which admittedly I still don't know the difference versus the generic [trunk-based development](https://trunkbaseddevelopment.com/). Given that Microsoft have hundreds of developers (and at the time of writing, our IT engineering department is well over 200) and we are also using Azure DevOps, most thought it is probably a good idea that we also use the same strategy that Microsoft has.

But changing our process for the sake of imitating a model organization or fitting ourselves around a tool seems like a lame excuse. So what exactly needs fixing?

## The GitFlow problem

One of my observations in using GitFlow is that it tends to have a lot and I mean A LOT of branches, some which are long-living, just to release a feature or issue fixes. Just take a look at this diagram:

<figure>
  <img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y9e3rkj9gktfxvo3zsiq.png">
  <figcaption>Fig1. GitFlow branching strategy. [Source](https://nvie.com/posts/a-successful-git-branching-model/)</figcaption>
</figure>

Having multiple branches isn't bad per se. In fact, GitFlow is great for simultaneously managing multiple versions, such as in our case, where we have different versions in production, UAT, and DevTest environments. I think GitFlow is really good at enabling developer independence and isolation of changes. That way, you can work with one version without worrying that the other versions will be affected.

But as our team and repositories grow, it became quite difficult to have a mental model of it. There were also occasions when our team forgot to merge the release branches back to master and develop. There is also a latency (for the lack of a better term) before the fixes issued in the release branches becomes available in the develop branch, where other developers are already working.

## Here comes the Trunk-based

If using GitFlow has become difficult, then why are we not willing to try a different strategy? Well, there's a couple of reasons but everything probably boils down to comfort.

### What's not comfortable?

Since we started migrating from *monorepo* to *service repo* (that's one repository per microservice), different squads can have their own branching strategy especially those that work exclusively with the backend services. Our squad decided to use GitFlow because we wanted to clearly separate the branch we are working on (develop) and those that are in different environments (release, prod/master).

This was not the case with our front-end teams as they have been using trunk-based development ever since (as what I've been told). And from different anecdotes around the office, we hear that they often have issues with some commits getting removed or replaced by accident. That's like reading bad user reviews on Amazon or [insert your favorite online marketplace here]. Can't expect us to be happy knowing that we're going to move to something that messy.

We also expect that there will be a learning curve in every adoption of a process or technology. While we welcome learning opportunities, at that time we were in the middle of multiple releases. Given the time that we have, inserting steps or modifying our existing processes doesn't sound justifiable if we just going to do it for the sake of compliance.

Then there's the notion of [cherry-picking](https://trunkbaseddevelopment.com/branch-for-release/#fix-production-bugs-on-trunk), which seems to be norm in trunk-based development. We are wary of using cherry-pick as it feels hacky and probably prone to mistakes. We also rarely use cherry-pick so again this is about the team not being comfortable with our level of knowledge on something.

### The transition

We merged our feature and release branches to develop, then merged develop to master. Develop is now deprecated and we will now be merging only back to master as it is now the trunkline.

The change wasn't sudden, and it took as weeks if not months before completely shifting to it. This is due to several releases at the time that has to be completed and merged back to master first. The sad thing was, as far as I know, that there was no concrete plan for the transition. Looking back, it probably was a good thing that we were left to do it at our own pace. With delivery deadlines approaching, we're probably more concerned with how the change would disrupt our timelines rather than the strategy itself.

Our squad at the time was managing about 7 repositories and they all have to switch to trunk-based. A bit inconvenient, yes, but something we are willing to take on in hopes of having a better workflow.

It probably won't be fair if I judge it just after a few weeks of use. So I'm gonna stop here for now and come back to this write-up after a few months...

![Many months meme](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w2w4d3cvy31s8dpwh7d4.png)
_(I actually forgot I was writing this, so it took longer than it should haha)_

### Our experience and some insights

It was not as chaotic as I expected, but it's definitely not the promise land we hoped it would be. One advantage that I see is that all of us can confidently pull from `master` every time, knowing that all the changes are always merged first to it. This solves the above mentioned problem where we sometimes forget to merge the release branch back to master.

The trade-off, however, seems a little too much than the benefits we're reaping. In the absence of feature flags, it's quite hard to manage which gets to production and which doesn't. Suppose there are 3 sets of code changes and let's call them **FeatureA**, **FeatureB**, **BugFixC.** FeatureA and FeatureB are independent features, while BugFixC is a fix issued to address the bugs found during [manual] testing. After applying the fix, **FeatureA+BugFixC** is ready to reach production but FeatureB isn't (i.e. because it hasn't gone through QA yet or some other sort of manual testing).

What happens is that we checkout a branch from FeatureA merge commit then we cherry-pick BugFixC to it. Perhaps not an elegant way, but this is the only option we know so far given that we haven't invested time to learn and develop our features around feature flags.

## Verdict

The truth is **I still don't know.**

This might be rather disappointing after the lengthy blabber but my knowledge of trunk-based development is severely limited to what we are currently doing in our squad. While some of my peers are convinced that trunk-based development is another cargo cult, I think that it is our own execution and development process that is failing us. I've talked with friends, former colleagues from other organizations who are currently using trunk-based development and they are finding success with it. So I'm leaning towards the possibility that we are really just not using it correctly and were unable to maximize its potential.

So are we going to continue using it? Yup, and I don't see us changing it anytime soon. Doing so will be another learning-curve that we have to overcome.

And we haven't even climbed this trunk yet.

<hr/>

## Notes and Tangential Thoughts

- Resistance to change might actually be a good thing. It makes us think about the implications thoroughly and it also shows that we really care about what we do.
- You may have noticed my usage of the term "squad". We are trying to adopt the Spotify-flavored agile. Whether that's a good idea or another cargo cult destined to fail is still subject for observation. Currently, there are a lot of difficulties and there seems to be a relapse to non-agile methodologies. I don't think we are doing it right (yet), which perhaps is the reason why we are also having difficulties with our branching strategy. Maybe our processes should mature first, then hopefully our branching strategy will soon evolve to fit our needs.

---
<br/>

## Relevant Articles

- [Trunk Based Development](https://trunkbaseddevelopment.com/)
- [Release Flow - Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/learn/devops-at-microsoft/release-flow)
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [Gitflow is a Poor Branching Model Hack](https://hackernoon.com/gitflow-is-a-poor-branching-model-hack-d46567a156e7)
- [Please stop recommending Git Flow!](https://georgestocker.com/2020/03/04/please-stop-recommending-git-flow/)
- [Git tips for trunk-based development](https://dev.to/alediaferia/git-tips-for-trunk-based-development-1i1g)

## Credits

- Cover photo by <a href="https://unsplash.com/@niko_photos?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">niko photos</a> on <a href="https://unsplash.com/s/photos/tree?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

<br />

> **Disclaimer**
>Views, thoughts, and opinions expressed in this text belong solely to the author, and not necessarily to the author's employer, organization, committee or other group or individual
