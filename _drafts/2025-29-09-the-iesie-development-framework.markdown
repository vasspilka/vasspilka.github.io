---
layout: post
title: "The IESIE Development Framework: Making Startup Chaos Manageable"
date: "2025-09-27 20:43:21 +0200"
---

If you've ever worked in a startup, you know the drill: new ideas flying around constantly, priorities shifting like sand, and everyone scrambling to build features that might completely change next week. After years of navigating this beautiful chaos, I've noticed something interesting—it's rarely the actual building that slows us down. It's the fuzzy space between "hey, what if we..." and "here's exactly what we need to build."

## The Real Problem with Moving Fast

Most startups I've worked with share a common pattern: they leap straight from a brilliant idea to writing code, skipping the crucial steps of careful planning and coordination. The result? Developers spend days building something, only to hear "that's not quite what we meant" right before they are about to ship. It's not that requirements changed because of new business insights, but rather nobody really understood what they were building in the first place.

This problem became crystal clear at my current startup, Teacherspace. With AI coding assistants now able to generate entire features in minutes, our old excuse of "development takes time" vanished. Suddenly, the real bottleneck was exposed: we weren't exactly sure of what needed to be built before we started building it.

## IESIE: A Framework for AI-Driven Development

After a rushed week of development we found out that a feature we just shipped did not quite hit the mark. The designs did not include some of the requirements and the final implementation was not quite what we wanted. There I realized something needed to change so after some brainstorming I developed what I call the IESIE Development Framework (pronounced like "easy"—because that's what development should feel like). It's designed to guide small product iterations—what we call Projects—from that initial spark of an idea all the way through to measuring their impact in production.

IESIE breaks down into five progressive stages, each building on the last:

### 1. Ideation: Where Everything Starts

This is the fun, messy beginning where someone on the team says, "What if we could..." Usually it's just one or two people with a spark of an idea. At this stage, things are rough and uncertain—and that's perfectly fine. 

The goal here isn't to have all the answers but to capture the essence of the idea clearly. We document three key things:
- **The problem**: What pain point are we addressing?
- **The rough solution**: How might we solve this? (emphasis on "might")
- **Why now**: What makes this the right time to tackle this?

The output? A simple one-pager that communicates the idea clearly enough that others can understand and engage with it. Nothing fancy—just enough to move forward.

### 2. Exploration: Reality Check Time

This is where the magic happens. The broader team comes together to poke holes in the idea (constructively, of course). Each perspective adds crucial context:

**Business asks**: "Does this create real value? Does it align with where we're heading?" If the answer is fuzzy, we dig deeper or pivot.

**Product explores**: "Will users actually care about this? How will it change their experience?" This often includes quick usability checks with actual users or customer interviews.

**Design envisions**: "What could this look like? How would users interact with it?" Early mockups help everyone visualize the end result and often reveal hidden complexities.

**Engineering investigates**: "Can we actually build this with our current setup?" Sometimes this means spinning up quick prototype spikes to test technical feasibility.

By the end of exploration, we've either validated the concept with enough confidence to move forward, some of the ideas will not make it past this stage, but that's fine, in fact that's great! It means we've just saved ourselves weeks of wasted effort by killing a bad idea early. Pass or not, both outcomes are wins.

### 3. Specification: Getting Crystal Clear

This is where we transform a validated idea into a detailed description we want to build. This can include designs, product specification, technical documents, and specific tasks that need to be done.

For best results the whole team needs to work together:
- **Business** helps define key success metrics and goals
- **Product** writes detailed requirements with clear acceptance criteria
- **Design** creates comprehensive designs in Figma 
- **Engineering** produces a technical design document outlining the solution approach
- **Project lead** breaks everything down into manageable tasks and tickets

This step has become increasingly important as AI tools change how we work. When coding assistants can generate features quickly, knowing exactly what to build becomes the real challenge. Good specifications make the difference between rapid progress or general confusion.

Well-written specs also serve a simpler purpose: they keep everyone aligned and give us something concrete to validate against. No more "I thought we agreed on X" conversations.

The level of detail needed varies by project, but generally, these questions should have clear answers: 
* Why are we doing this? (the business value)
* What exactly are we building? (the scope)
* What will it impact? (dependencies and side effects)
* How does it work? (technical approach)
* How does it look? (user interface)
* How do we measure success? (metrics and KPIs)

The whole team then aligns on the deliverables—documents, designs, tasks. This doesn't mean every detail is set in stone. Even with careful planning, unexpected situations will arise. What it does mean is that we've minimized the risk of building the wrong thing due to miscommunication. 

When those unexpected details surface during implementation, we update the specification. Think of it as living documentation that evolves with your product—a reference for how everything actually works.

An equally important part is breaking down the work into specific tasks. By the end of specification, the project should be sprint-ready with assignable tickets that developers can pick up and run with.

Not every project needs every deliverable. A small technical improvement might just need an engineering doc and some tasks. A new user-facing feature probably needs the full treatment. Use your judgment, but err on the side of over-communication.

### 4. Implementation: Where the Magic Happens

This is the part everyone thinks of as "the real work"—writing code, configuring systems, and bringing the idea to life. But if you've done the previous steps right, implementation becomes surprisingly smooth.

The team works through their tasks in sprints, handling all the usual suspects:
- Writing and reviewing code
- Setting up infrastructure
- Coordinating with external services or partners
- Running tests and QA cycles
- Validating performance and security concerns
- Finally, releasing to production

What makes this stage different in IESIE is that developers aren't constantly asking "wait, what are we building again?" The specification phase already answered those questions. This is especially powerful when working with AI coding assistants—feed them a well-written spec, and watch them generate exactly what you need.

### 5. Evaluation: Closing the Loop

Here's where most frameworks fall short—they ship and forget. Not IESIE. The evaluation stage is about making sure we actually delivered value, not just code.

We start by checking our work against the original specifications and those success metrics we defined earlier. Did we hit our targets? If not, why? This isn't about blame—it's about learning.

We also build in buffer time for the inevitable post-release adjustments. No matter how well you plan, users will find edge cases, or you'll discover that button should really be blue, not green. Having dedicated time for these tweaks prevents them from disrupting your next project.

Most importantly, we gather feedback from actual users. Sometimes a feature that seemed perfect in our heads falls flat in reality. Other times, users love something we thought was just okay. These insights help us generate new ideas, creating a virtuous cycle of IESIE development where Evaluation bring Ideation.

## Why This Isn't Waterfall 2.0

I know what you're thinking—"This sounds suspiciously like waterfall." But there's a crucial difference. IESIE is built for small, fast-moving teams where everyone collaborates throughout the process. Instead of requirements flowing top down, we have the whole team contributing. Developers, designers, product folks, anyone can bring ideas with Ideation and everyone needs to work together during Exploration and Specification.

We're also talking about bite-sized projects here. Each Project should take anywhere from two weeks to two months, we should never expect years-long death marches of traditional waterfall. If your project can't fit in a that window, break it down further.

Most importantly, IESIE is designed for our new reality where AI assistants can turn a good specification into working code in minutes. The bottleneck has shifted from typing speed to thinking speed, and our processes need to catch up.

## The Beautiful Cycle

What makes IESIE particularly powerful is its cyclical nature. The evaluation stage doesn't just close out a project—it sparks new ideas. You discover that users are trying to use your feature in unexpected ways, or that solving one problem revealed three more interesting ones. These insights flow right back into ideation, and the cycle begins again.

This creates a sustainable rhythm for innovation. Instead of the exhausting sprint-crash-sprint pattern many startups fall into, you get a steady flow of well-thought-out improvements, each building on the lessons of the last.

## Does It Actually Work?

At Teacherspace, we've been using IESIE for our last several projects, and it's been helpful. We've reduced those energy-draining moments where a completed feature needs to be rebuilt because of miscommunication. Our developers are happier because they're not constantly dealing with shifting requirements. Our product team is more confident because they can see ideas properly validated before committing resources.

Are we perfect at it? Not even close. We're still figuring out how to make evaluation more systematic, and sometimes we catch ourselves trying to skip steps when we're excited about an idea. But that's the beauty of a framework—it gives you something to improve against.

## What Do You Think?

IESIE has helped us at Teacherspace, but I'm under no illusion that it's the perfect solution for everyone. Every team has different challenges, different dynamics, and different needs. What works for us might need tweaking for you—or might not work at all.

If you do want to give it a try, here's what worked for us:
1. **Start small**: Pick a low-risk project for your first run
2. **Adapt freely**: Skip steps that don't make sense, add ones that do
3. **Give it time**: It took us 2-3 projects before it felt natural
4. **Share what you learn**: The framework gets better when teams share their experiences

I'd love to hear your thoughts. Does this resonate with challenges you're facing? Have you tried something similar? What's worked (or hasn't) for your team when managing the chaos of startup development?

Maybe your team has already solved these problems in a completely different way—if so, I'd be curious to learn about it. After all, the best frameworks are the ones that evolve through real-world use and feedback from teams in the trenches.

Feel free to reach out with your experiences or questions. Who knows? Your insight might be exactly what helps IESIE evolve into something even more useful.