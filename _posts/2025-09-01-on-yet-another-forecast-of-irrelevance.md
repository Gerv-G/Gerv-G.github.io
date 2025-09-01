---
title: On Yet Another Forecast Of Our Irrelevance
date: 2025-09-01
categories: [SoftwareDev]
tags: [career, artificial-intelligence, software-engineering, product-engineering]
---

Three scores and six years ago, our fathers brought forth to this digital world a new language, conceived in business, and dedicated to the proposition that all men can code.

That language was COBOL, introduced with the promise that non-technical professionals could write software using syntax closely resembling everyday English. CODASYL did a great job in designing the language and it stood the test of time.

But the idea of empowering *anyone* to write it fell short, as evidenced by the shortage of COBOL developers still needed to maintain legacy systems that still run mission-critical financial software.

Fast-forward a few decades later, I was sitting in my high school computer class, writing HTML for the first time. I hated it. Surely there had to be an easier way, maybe some kind of GUI where I could just drag things onto the page? When I asked, my teacher deadpan replied, “Oh, that exists. It’s called Dreamweaver but you’re not allowed to use it.” She basically dangled the promise of modern convenience in front of us and then snatched it away, which I can only assume was part of some elaborate teacher hazing ritual. And so, I begrudgingly went back to hammering out HTML, one tag at a time, muttering “I wouldn’t be doing this for a living anyway”. After all, my grand plan back then was to study political science and law. (Narrator: …and that didn’t happen)

But it wasn’t until the late 2010s, during a job orientation, that I learned of the term *low* *code* and its sibling *no code.* These are tools that allow one to build software with little to no code (duh). The main point is to minimize the need for code and the developers that will write or maintain them. Of course, none of these ideas were really new. I mean, look at all those slow-moving [Excel sheets](https://www.wsj.com/articles/sorry-ai-old-school-spreadsheets-are-still-king-cbb99936) humming away, running key business functions like ancient engine generators holding up the grid - none of that really required developers. But the way it was pitched to us back then, no-code/low-code wasn’t just a handy shortcut, it was the future.

![future](https://media1.tenor.com/m/Vi0AbgoMvXAAAAAC/future-spongebob.gif)

Now there’s a new kid in town: AI. Or if we’re being pedantic, LLMs, as AI to some capacity has been around for ages. It’s just that LLMs drastically pushed it to new heights particularly in [natural language processing](https://en.wikipedia.org/wiki/Natural_language_processing), which enables it to accurately use human languages, programming languages included. So, people have started to leverage AI and hailed it as the messiah. The once esoteric art of making a computer do thy bidding is no longer reserved to us glasses-wearing coffee addicts.

As a natural consequence, companies have started shifting toward more AI-centric workflows, which means they need fewer developers. It also doesn’t help that the global economy has been struggling, leading to waves of layoffs across the tech industry. 

Once again, many are predicting the demise of software developers. But just as quickly, skeptics push back, pointing to the many moments in the past when the profession was supposedly under threat, only for it to adapt and persist. LinkedIn became a battleground.



> When AI started gaining traction, so did the number of people rushing to LinkedIn <br/>
> Using one sentence per line <br/>
> To boldly announce that it’s “revolutionizing software development.” <br/>
> Because buzzwords are free. <br/>
> And hot takes get engagement. <br/>
> Never mind that most posts say the same thing with slightly different emojis. <br/>
> Or that real-world solutions require nuance <br/>
> <br/>
> (insert hashtags here)

Kidding aside, it was fatiguing to hear about it almost every day. I appreciate the effort in thought leadership and I do pick up nuggets of wisdom from time to time. It’s a different story when every tech bro starts acting like they’ve uncovered the holy grail.

But somewhere between genuine curiosity and a healthy dose of FOMO, I took a step back to evaluate whether the hype around AI truly held weight. Not out of arrogance and not as an attempt to be contrarian, but because I believe it’s important that each of us form our own understanding rather than riding someone else’s echo.

So I vibe coded… 

## Not All Vibes Are Equal

When I first came across the term *vibe coding*, I instantly dismissed it as just another Gen Z slang and thought it was ironic, since the term itself felt like the kind of thing they’d call *cringe*. Well, these folks were quick to correct me that it was actually [Andrej Karpathy who coined the term](https://x.com/karpathy/status/1886192184808149383?lang=en). I guess that’s what happens when we millennials try to mingle with the GenZs.

There’s been, and still is, a lot of noise around the term, because of course, it’s ✨AI ✨. And as with anything AI, it was being used as a panacea. But lately, I’ve noticed it’s being thrown around more often in a not-so-kind fashion. Now, *vibe coding* is often used as a jab, suggesting someone is hacking away without structure or standards, producing code that “just works” but barely holds together. Whenever I encounter such in the communities I am in, I would jokingly say “ouch”. What I found out is that we define vibe coding slightly differently.

![I'm something of a vibe coder myself](/assets/img/on-yet-another-forecast-of-irrelevance/im-something-of-a-vibe-coder.png)

Having used AI in my workflow for close 2 years now and looking at it in retrospect, I think vibe coders go through these stages:

### Stage 0: The Armchair Skeptic

*“It’s just autocomplete on steroids”*

These are those that immediately rejects AI, regurgitating criticisms against it without personally trying it out. This is where I was when ChatGPT first came out.

### Stage 1: The Trial User

*“Okay, I’ll try it... just to see what the fuss is about.”*

The curious cats who just want to see if it's leap and bounds beyond the chatbots like [Eliza](https://en.wikipedia.org/wiki/ELIZA) or those of early 2010s like [Simsimi](https://en.wikipedia.org/wiki/SimSimi). People in this stage also checks if it passes the [Chinese Room Argument](https://en.wikipedia.org/wiki/Chinese_room) or the [Turing Test](https://en.wikipedia.org/wiki/Turing_test)

### Stage 2: The Migrant

*"It’s not perfect, but hey, it saves me a trip to Google or StackOverflow.”*

The ones who are (hopefully) over the [peak of inflated expectations](https://en.wikipedia.org/wiki/Gartner_hype_cycle). They start to understand that AI is a very powerful tool in extracting information over the internet.

Why rummage through hundreds of closed posts or dead forums when you can get the same snippet you need from AI in seconds? You can even have it summarize the official documentation!

### Stage 2.5: AI Take the Wheel

*“Oh sh*t this is great. Gimme more!”*

With the introduction of agentic AI, we can now go beyond simple Q&A. We can now just tell AI what to do.

I think is what most of the slander on vibe coding comes from. A lot of users get stuck on this mentality and just purely rely on AI.

I suppose non-technical folks and programming novices are more susceptible to this as they don’t know the intricacies involved in software development yet. Not exactly their fault with the way AI is being marketed. But the onlookers are rarely so forgiving when they see code that seemed to be so haphazardly written. 

Experienced developers are no exception. It’s very easy to give the reins to AI after giving it instructions. Heck, you can [give AI the story itself](https://www.anthropic.com/claude-code) and it can code it for you. After all, who doesn’t want to be relieved of the suffering we created for ourselves? Less head scratching, ain’t it?

But this paradise might be a hell in disguise. Weak security and poor system design are all valid criticism of this vibe coding stage. Last July, an [AI wiped out a database](https://fortune.com/2025/07/23/ai-coding-tool-replit-wiped-database-called-it-a-catastrophic-failure/). That already paints a grim picture of what could go wrong when we leave everything to AI.

So the more you use it, the more you (should) understand its flaws and its gaps. And that’s where you, the developer, should come in.

![Fine, I'll do it myself](/assets/img/on-yet-another-forecast-of-irrelevance/fine-ill-do-it-myself.png)

### Stage 3: The Taskmaster

At this stage, you are more or less familiar with the extent of the powers AI has.

You give it precise instructions to rapidly scaffold. You tell it to follow certain patterns, use existing conventions in the codebase, and respect architectural boundaries. You bounce ideas off it, recognize when it’s patronizing you, and even argue against its approaches.

You got yourself a pair programmer: you are the navigator, and the AI is the driver, but you don’t mind stepping in to fix what it wrote or taking over yourself.

---

**However, one may argue: that’s just how it is right now. AI is getting better and better at understanding context and extrapolating from that. It is not a matter of if, but when, the AI will be smart enough to do everything in its own. So what happens next? Will we be jobless?**

## What Does My Crystal Ball Say

I have always found it amusing, baffling, and now increasingly unsettling, that our industry is ironically obsessed with getting rid of the developers. I don’t think I’ve seen such a push in other fields. I wouldn’t want my doctors or lawyers replaced by AI. Would you?

Still, the industry *seems* to be dreaming of a developer-free world. Well, I guess we can always go back to [farming](https://www.linkedin.com/posts/thatstraw_this-man-resigned-from-microsoft-after-22-activity-7191439612781740032-Gmfn).

![The future is clear. It's going to fall apart](/assets/img/on-yet-another-forecast-of-irrelevance/future-fall-apart.png)

Sorry, I don’t actually have a mystical future-seeing orb. What I do have is a glimpse of an underexplored path we’re already on.

We are problem-solvers through and through, which is why I prefer using the term “engineer” even when some disagree (e.g. [Exhibit A](https://www.theatlantic.com/technology/archive/2015/11/programmers-should-not-call-themselves-engineers/414271/), [Exhibit B](https://medium.com/@tsecretdeveloper/we-are-not-engineers-5fabbdda6a51)) - a topic I want to cover some other time.

To me, engineering is the art of managing trade-offs. We don’t get to design solutions only for the ideal scenarios. We need foresight to anticipate the messy real-world constraints and judgment to balance requirements against limited resources.

Now that we stand on the precipice of a future where our technical expertise may be supplanted by the ever-faster AI models, I believe **our role will evolve from software engineers to product engineers.**

## AI Can Build. We Must Engineer.

When I got my current job 3 years ago, I was surprised to find that my onboarding tasks included a book. It’s called Raving Fans, which is a uhhh… about customer service? Why on earth would I, a software engineer, need to care about that? As a non-reader, I immediately panicked. What if I couldn’t finish it in time and failed onboarding before I even began?

![My copy of Raving Fans](/assets/img/on-yet-another-forecast-of-irrelevance/raving-fans.jpg)

Luckily, it’s a very short book. Short enough for someone like me, who couldn’t even stay put during meetings, to finish it in one sitting. Honestly, I’m impressed myself.

I finished that book mostly just to get it over with. Sure, I caught a whiff of the ideas — customer-centricity, finding problems worth solving, yada yada — it all reminded me of my design thinking and technopreneurship class in uni. But they weren’t things I think about on a day-to-day basis. I was too busy wrestling with code to worry about “delighting customers.” My dear product managers would probably be heartbroken if they saw this post.

Turns out, that little book was foreshadowing of where my role might be headed.

With every leap forward, it’s harder for us engineers to ignore the question of how we can stay relevant when the machines finally *out-code* us. Actually, they may already be doing that. Recently, life has steered me right back into these thoughts.

For one, I was put into a team where our job isn’t just to draw boxes or push code. We’re tasked to explore problem spaces and spin up quick prototypes to test the potential solutions. If they’re any good, we iterate, maybe refine, and prepare for productisation. Otherwise, we pivot or throw them away.

Around the same time, and forgive me for flexing a little, I got a CTO friend (I mean we’re now FB friends at least, we must be friends, right?). There was this time we were discussing in [Pandesal.Dev](https://discord.com/servers/pandesal-dev-748554476398444635) about engineering and entrepreneurship. He is trying to encourage everyone to [try having their own startup](https://substack.com/home/post/p-169711242). I told him it’s not something I’m fully convinced yet. Very early on in my career I’ve already decided that I’m an engineer not an entrepreneur.

As I build these prototypes, I realized I have been leaning so much on AI. I wondered if I’m getting dumber and whether I am writing myself out of a job. But it was also then that I remembered that I am not here to just write code.

I’ve always preached that software engineering is way more than that, but it is only now that I’m coming to my senses. Having AI by my side has allowed me to pour some of my brain power into [thinking more about the product holistically](https://www.atlassian.com/agile/product-management/product-engineering).

In case you’re lazy and doesn’t want to click that link, simply put a product engineer is someone who doesn’t stop at “how do we build this?” but also asks “why are we building this?” and “who is it really for?” It’s about complimenting our technical skill set with product sense, user empathy, and the ability to weigh trade-offs beyond just the code.

I’m only just starting to make that shift myself. These days, I try my best to think less about the technical aspects and more about the shape of the problem, the customer need, or the experiment we’re really trying to run. And I’m grateful, honestly, that I happen to be in a team and role that gives me the space to practice that muscle.

So maybe I’m finally living up to the thing I’ve been shouting for a while now, that we should all be product engineers. At least now I can say it without being a complete hypocrite.

![We must be better](/assets/img/on-yet-another-forecast-of-irrelevance/we-must-be-better.png)

While my adventure is far from over (I hope), I already feel like I’ve come back carrying a small elixir: a reminder that our careers may not be in danger but it is nudging us to not cling on the keyboard and start seeing with a wider lens. The future of engineering isn’t just in the elegance of our code or the brilliance of our architectures. It’s also in how well we connect those to real problems and real people. The mindset of a product engineer will help us stay relevant long after the AI can outperform us. It has been said again and again, that AI is a tool, but I’d also like to add that it is not an antagonist as some portray it to be (well, at least not until Skynet finally goes live).

So your next mission, should you choose to accept, is to expand how we think about our **craft**. The future won’t wait and neither should we.
