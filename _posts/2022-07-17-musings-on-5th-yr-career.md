---
title: Musings on my 5th year as a Software Engineer
date: 2022-07-17
image:
  path: https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F5vrtu3hmi31ea96chv92.jpg
  canonical_url: https://dev.to/gervg/musings-on-my-5th-year-as-a-software-engineer-5dcn
categories: [SoftwareDev]
tags: [career, retrospective, software-engineering]
---

I still remember my first day on the job. From the bus stop, I walked under the summer’s day heat dripping with sweat in my button-up shirt. And as I reach the surrounding buildings, I had hoped to seek comfort in the shade and breeze. But I was instead welcomed with what felt like a hot humid breath. Finally, there I was at the office door looking like I overcame an hour of trekking - not the first impression I wish to make. At that point, I’m no longer sure if I was sweating because of the weather or because of nervousness.

You see, I never planned to be a software engineer (but that’s a story for another day). Heck, I don’t even know what “software engineering” was. All I knew was that these were people writing code for a living. So I wasn’t really confident I could stay in this field for a long time.

But few months ago, I hit a milestone - I’m now in my 5th year in the industry working as a software engineer. While that may not seem much in the grander scheme of things, I still would like to take this opportunity to look back and share my experiences. Since I don’t think I can exhaustively list all my learnings in a single post, I just decided to make a summary of my thoughts, opinions, and probably some bits of wisdom I picked up in the past 5 years. I divided them into three categories as follows:

- [Career](#on-career) - general stuff that I have learned so far in my career progression
- [Way of Working](#on-way-of-working) - the nuances of working with other people and the software development process
- [Software craftsmanship](#software-craftsmanship) - the tacit knowledge that influences me on how I write software

The bullet points below are not written in any particular order. You may simply skim through them and pick up whichever you think interests (or intrigues?) you.

## On Career

- The university where you graduated from no longer matters after your first job.
- Education and skill development does not stop once you leave the four corners of the classroom - it’s a life-long commitment.
- Be updated on the trending technologies but no need to dive deep into each one of them. [Just-in-time learning](https://en.wikipedia.org/wiki/Just-in-time_learning) is enough
- Just because you love building software doesn’t mean you need to be the next big technopreneur. It doesn’t hurt if you really want to be one but it’s not the only path you can take.
- Job titles didn't matter as much as I thought they would and are not always indicative of one’s experience/talent.
- Debating about the difference between engineer, developer, programmer, coder, etc. is a moot point. Each person will have varying specializations and level of experience.
- Learn the market average for the position you are applying for.
- Do not overly boast your accomplishments as they may come off as annoying if not rude, but do not undersell your contributions either. *Brag responsibly* as I would say.
- Don’t accept jobs without a formal contract or working agreement, and carefully read the clauses.
- If you have the time and resources to get them, certificates are nice.
- You don’t need to write code on weekends just to tell yourself that you’re a good developer.
- Create healthy relationships with your colleagues and build your network.
- Join and engage with software development communities
- Good performance at work is a by product of good personal development - don’t stop learning stuff may it be technical or soft skills.
- Soft skills are just as important as technical skills.
- Do not be afraid of finding new opportunities for career growth. But also do not jump so frequently as you will not experience how to handle a maturing product or service.

## On Way of Working

- That I won't be writing code all the time. Software engineering is multi-faceted and its art goes beyond just programming
    - much of the work involves talking with the stakeholders and decision-makers
    - managing work for yourself and sometimes even for your team
    - negotiating the scope, forecasting work, managing expectations
    - designing the system such that it is maintainable, scalable, secure, etc.
    - supporting what you release in production
- Agile is an ideal, but the journey to it is an arduous and sometimes disruptive one
    - it requires conceptual integrity on what it means to be "agile"
    - the whole organization has to be on board and supportive
    - it is not a single defined process but an exploration of what works best for your team
        - but change can be difficult to adapt and may initially slow down progress
- A team is not just a bunch of individuals working on different parts of a single system. A healthy team is one whose members are willing to go beyond the *self* mentality and are mutually committed to a common purpose or goal. It should be no silos.
- Software development is a collaborative effort rather than a mere collection of individual contributions. The stereotype that developers are lone wolves is not true.
- Estimations are *effin* hard, especially in the face of the unknown. Oftentimes, you’d find yourself not knowing what you don’t know about a particular problem - worse you may not know what the problem is at all.
- Software engineers are passionate and strongly opinionated people
    - We care so much about how to do it the *right* that [disagreements have become a natural part of the process](https://en.wikipedia.org/wiki/Tuckman%27s_stages_of_group_development#Storming). It doesn’t mean it’s toxic though.
    - Software engineering requires careful assessment of pros and cons - there will be no single correct answer
- Pull requests should be egoless. It is an opportunity for discussion and knowledge sharing.
- Explicitly advocate for safe space. This will help empower team members to share ideas, ask questions (even if they’re silly), or try new things while also leaving ample margin for errors.
- Maximize the tools (i.e. a ticket tracking/project management system) you have in your team for documenting stuff. This will help give context to what a particular item is and is useful for asynchronous communication.
- If your process involves a lot of grunt work, look for ways to automate it so you or your team can focus on other stuff.

## Software Craftsmanship

- Software development is a web of unknowns and possibilities - there will always be scenarios you’ve never anticipated and trade-offs you never accounted for.
- No software is bug-free
- The best tool is often one that you already know how to use. Conversely, *if all you have is a hammer, everything will look like a nail.* Therefore, don’t just learn the tool. Understand the specific problems it is trying to solve.
- Code style depends on the team and the language conventions. What's easy to write or read for me may not be the same for everyone. When working with a team, it is important to establish this as early on and enforce it (i.e. linters, hooks, static code analysis tools, etc.). This will help improve consistency throughout the code base and possibly reduce cognitive load as everyone will know where and how to look for something.
- Code is read much more than it is written. Remember that you are writing code for another person to read later.
- Familiarize yourself with some of the popular language paradigms and type systems. It would make switching easier. And when writing, you may also start borrowing elegant concepts from one language to another
- Learn a version control system. *Git gud* (pun intended)
- Learn your editor/IDE. It’s your most important tool. Customize/configure it to your liking to improve your workflow
- Debugger is your best friend
- Logs are essential but overdoing it may create too much noise. Investigation of issues may feel like looking for a needle in a haystack.
- You will never have dedicated time to refactor something. If you can **safely** and **timely** refactor something, refactor it now
    - easier said than done especially in legacy systems that can sometimes be too fragile
- On writing tests:
    - Tests are akin to mathematical proof. If you declare that something behaves as such, then you have to prove it
    - Tests are safety net for the next developer that will change something. This will ensure that the previous behavior of your system remained intact
    - Tests can also serve as a form of documentation as it is a collection of *facts* about a system
    - Writing tests can be expensive, but the bug fix turnaround time can be more expensive. Write tests whenever you can and wherever
    - TDD is a powerful design tool, but it is not about unit testing
    - You don’t always need to do TDD especially when you already have a clear idea of the design and what steps to take to implement it
    - Mocks are helpful but are also easily misused. Use them sparingly
- Knowledge and application of design patterns can be a *chicken and egg* problem. Learning a design pattern might make you apply it to problems it doesn’t fit in. On the other end of the spectrum, not knowing any design patterns will likely make your code less organized and less maintainable. A possible solution is to work with your team, discuss the pros and cons, and let a design emerge.
- Premature optimization is bad, but that does not mean you’ll willingly write an obviously slow code. Do not let it be an afterthought. As mentioned earlier, conduct timely refactoring and make it sufficiently performant.
- Do not cling to popular conventions or approaches if it doesn’t work for your team lest you be a victim of *cargo cult*. And that includes this blog post - don’t just believe everything I say. Critical thinking is necessary in order to achieve solutions that fit the context of your problem. [There is no silver bullet](https://en.wikipedia.org/wiki/No_Silver_Bullet)

## Credits

- Cover photo by [Greg Rakozy](https://unsplash.com/@grakozy?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/milkyway-man?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
  
