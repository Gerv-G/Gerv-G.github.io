---
title: Newbie Anew
date: 2022-07-17
canonical_url: https://dev.to/gervg/newbie-anew-5101
categories: [SoftwareDev]
tags: [career, software-engineering, retrospective]
---

I always tell people that “new things” make working in software development constantly exciting. And when I say new things, I just don’t mean bleeding-edge technology. I mean new problems, new approaches, or new patterns - even if they are just new to the person. What I have not told them is that with these exciting opportunities comes the nerve-wracking ordeal of facing unknowns.

When I was writing my [5th-year retrospect]({% post_url 2022-07-17-musings-on-5th-yr-career %}), I felt like I knew a lot. I thought I had already reached a certain level of mastery that would make me qualified to share my knowledge and experiences. And it was around the same time last year when I started a new job. That’s when I realized that *I don’t know sh*t*.

It was overwhelming, to say the least: different domain, tech stack, people, and culture. There were times when I felt dumb and undeserving to be there. Impostor syndrome perhaps? But…

![Impostor syndrome comic](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vyxwxyevvdr5r3tav030.png)
_Artist: [Gemma Correll](https://twitter.com/gemmacorrell/status/1441500836840886275)_

And since it's time for a "year in review" post anyway, I sat down and looked back at the struggles I had and the steps I’ve taken so far.

## Unfamiliar Domain
I previously worked for a digital bank for 3 years, and I more or less became the *de facto* subject matter expert on a few of our microservices. While I did enjoy being the go-to person, I eventually hit a point where I began wanting to try something different.

Which brought me to my current job at an HR tech company.

I was excited of course, but I was not prepared to be hit like a truck. Many foreign concepts were being discussed during meetings and I found myself there sitting clueless.

What we devs rarely talk about is that half of our job is actually understanding the business domain. We would often talk about the latest, fastest, or most elegant tech stacks and patterns. But at the end of the day, what we really want is simply a software that delivers value to our users. And we can’t do that if we do not understand the contexts it will be used in.

To fill in these gaps, I had to ask a lot of who, what, where, when, and whys. Fortunately, my team was very understanding and welcoming. It took me some time until I gained some confidence. Until now, I don’t think I’ve already understood everything yet, but it was a significant progress from where I was a year ago.

## The Mystery That Is Frontend

I **was** of the opinion that fullstack devs don’t exist (might be a good topic for a future post). Yet I am now working as a fullstack dev.

![Meme - Emperor Palpatine saying ironic](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hwwecj8izru8lnrc0y56.png)

I have been a (mostly) backend developer since the start of my career and the last time I touched frontend code was back in 2018. Even then, I was only exposed to JavaScript and a bit of JQuery. I know nothing about all these frameworks, tools, etc. What’s NodeJS? What’s NPM? What’s Babel? Webpack? What is this React thing? What’s with React vs Angular? ECMAScript? Typescript? 

… and the list goes on. The landscape of front-end development is truly intimidating.

I’ve heard these things before, but I never had to learn any of them because I don’t need them for work. I am passionate about my career, but I don’t really like spending weekends learning things I probably won’t need. Do I regret it? Yeah, a bit. I may have unintentionally limited my “horizons” so to speak. But I am relatively quick to learn things when I have something I need them for. If I had studied these technologies in the past and not used them, I probably would’ve forgotten them anyway.

Another _paradigm shift_ I had is the mental model for states. In backend, services are stateless - things go in, and things go out. The services themselves don’t get mutated nor do they have to “remember” what they did previously (well, technically they do with the help of the persistence layer but that’s not my point). In contrast, frontend components maintain states: Is the drawer open? Should I show the popover? Does the color change if <insert some event here>? These are things that I can’t simply think of as input → output models.

Luckily, I was able to get by after learning React hooks and a fairly easy-to-use state manager called [Zustand](https://github.com/pmndrs/zustand). I think I understand them well enough to deliver features or issue fixes, but I do know for a fact that I haven’t really grasped React’s component lifecycle. Maybe I’ll seriously study it one of these days.

CSS, however, remains to be the bane of my existence.

![Meme - The Babadook "why can't you be normal" but with CSS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kica4ujuuw0r1j1t3sqo.png)

## Cloud isn’t about rain

It is somewhat annoying when a new tech is hyped and rapidly gains a following. I don’t hate the tech, but I hate it when people throw around buzzwords all the time. It does the opposite effect on me, and I very quickly lose interest in it.

Cloud is one of them. I was still in college when I first heard about it. To me, it was just a marketing ploy. Just another term for servers you’re renting. That metaphor still kinda stands, but my arrogance kept me from understanding how much the tech has matured.

Like in the case of front end, it just stayed in my periphery. I had experience with some [cloud-native technologies](https://www.cncf.io/projects/), but a lot of the nitty-gritty details were abstracted to me because we had a dedicated DevOps/SRE team in my previous job. I never really had my hands dirty in writing infra definitions from scratch (I shamelessly copied YAMLs from existing projects) much less in deploying resources to the cloud (CI/CD pipeline has already been setup; everything is magic).

Enter: AWS - one of the most popular cloud service providers. It’s the platform that we’re currently using.

And I don’t know sh*t about it.

![Periodic Table of AWS](https://www.awsgeek.com/Periodic-Table-of-Amazon-Web-Services/Periodic-Table-of-Amazon-Web-Services.jpg)
_Periodic Table of AWS by [AWS Geek](https://www.awsgeek.com)_

The number of available services is just mind-blowing.  What the heck are all these? Which one do I pick?
![Meme - John Travolta lost in Target](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yf52ba5b81osagx9ei98.gif)

Luckily, we already have some existing in-house tooling that helps us use AWS and spin up our own services (for development purposes). It abstracts some stuff too so learning how to deploy an infra becomes a little less intimidating. I’ve also developed a rough mental model on how different services are _connected_ to one another. Gotta give props to Amazon for making their suite of services cohesive (CDK docs are kinda bad though).

## On hazy thoughts, accents, and stutters
We, Filipinos, always had a weird relationship with the English language.

It’s taught to us since kindergarten and we’re exposed to it in media. Despite the expectation of fluency, only a few regularly speak it outside of academic institutions or corporate settings.

I still struggle a lot. I get very conscious and anxious about my grammar and word choices. I find it very difficult to express what’s in my head clearly and succinctly. Even more so now that I have teammates who are of different nationalities, some of which has English as their native language. Add to that the differences in accents which I don’t have the ear for yet.
![Meme - dumbfounded smiling dog](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/febb8amggb6k85v8pbh0.png)

It’s quite ironic that our work, whose requirement is to have expertise talking to computers, is also very collaborative in nature. We have no choice but to communicate with our teammates and stakeholders regularly. You see, talking to a computer is very precise. It does exactly what you tell it to do. The intricacies of human conversations, like idioms, slang, and tone, are not present in programming languages. I don’t have to think about my or their emotions. Nobody has to assume intent behind the words. And certainly, no one has to guess what will happen if they say one thing and not the other.

![Meme - smiling when talking to a computer; disappointed when talking to humans](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1kgkugyh8p063uw04b3l.png)

Being an introvert, I blamed my personality for the gaps in my communication skills. But lately, I have been thinking maybe that’s not the case.

Recently, I’ve met my teammates and a few others in the office (oh hell yeah, I finally touched some grass after 3 years of working from home). Our interactions made me realize that I just needed something that would pique my interest then I would start pouring out everything from my mind, asking questions, and talking endlessly.

One feedback that stuck with me is that I need to be more confident in articulating my ideas. I think that hit the bull’s eye. It takes me a long time to arrange my thoughts, and I feel very uncomfortable with the silence in between. Because of that, I get thrown off and I start speaking even when the things I like to say haven’t been formed yet. The result: stutters.

I don’t think I’ll get over this wall anytime soon, but I’ll keep trying anyway.


## AI craze

Of course, this blog post won’t end without a single mention of this year’s AI craze that captured the attention of everyone, may they be in tech or not.

While most people are busy arguing whether AI will take our jobs or not (they won’t at least not anytime soon, but that’s a topic for another day), I am more concerned about how I am going to utilize it to speed up my work.

I was reluctant at first because I thought it was just another overly hyped technology. But there’s also a very strong “fear of missing out” feeling as I see my colleagues rave about it. To my surprise, it really gave me useful answers. Though they aren’t perfect and by no means you could start a multimillion-dollar startup company by just copying code from ChatGPT, it did help reduce the head scratching and typing for boilerplate code.

Fast forward to a couple of months, I find myself using it a handful of times in a month. Not quite sure if that’s too much or too few. It seems very useful when you’re too lazy to read the docs or when your google-fu isn’t enough to get you the right answer quickly.

And since I suck at closing paragraphs, [here’s one written by ChatGPT](https://chat.openai.com/share/7ddbbab8-854e-4f21-b6ea-cf8c216a0632):

> In reflecting upon this transformative year as a software engineer, I've navigated through uncharted territories, from delving into unfamiliar business domains to grappling with frontend technologies and cloud services. Each challenge became an opportunity for growth, and while I initially stumbled through the intricacies of communication, I've learned to adapt and improve. This retrospective journey underscores not just the hurdles but the continuous strides forward. Embracing the discomfort, I've cultivated a resilience that fuels my passion for learning. As I stand at the intersection of challenges conquered and those yet to be faced, I am reminded that the essence of this journey lies not just in overcoming hurdles but in the relentless pursuit of knowledge and progress. The coming year holds the promise of further evolution, and I am eager to embrace it with the same curiosity and determination that defined this transformative chapter

That sounds like a student trying to reach the minimum word count. I guess I’m not the only one struggling with communicating, eh?


## Credits

- Cover photo by [Mick Haupt](https://unsplash.com/@rocinante_11) on Unsplash

_P.S. I had this in drafts for a long time and had already lost the source of the image. So I reverse image searched this and found an [interesting interpretation](https://www.reddit.com/r/Jung/comments/hnmayo/a_classic_example_of_the_shadow_self/) of the image. I think that kinda fits with this post's theme_
