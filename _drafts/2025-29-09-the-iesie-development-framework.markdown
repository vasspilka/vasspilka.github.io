---
layout: post
title: "The IESIE Development Framework: Making Startup Chaos Manageable"
date: "2025-09-27 20:43:21 +0200"
---

If you've ever worked in a startup, you know the drill, new ideas flying around constantly, priorities shifting like sand, and a lot of scrambling to build features that might have different requirements next week. After years of navigating this beautiful chaos, I've noticed something interesting, it's rarely the actual building that slows us down. It's the uncertain space between "hey, what if we..." and "now we know exactly what needs to be build."

## The Real Problem with Moving Fast

A common theme in startups is that they leap straight from a brilliant ideas to writing code, this can be very rewarding when the idea is clear in the coders head. Unfortunately the reality is that it's hard to form clear ideas, and it get's much harder when we have to communicate them to someone else. When startups skip the steps of careful planning and coordination the result is often that developers spend days, sometimes weeks building something, only to hear "that's not quite what we need" moments before the deadline. It's not that requirements changed because of new business insights, but rather nobody really understood what we were building in the first place.

This becomes more obvious with AI coding assistants, now that we are able to generate entire features in minutes, with clear goals and alignment one can do a weeks work in a day. Our old excuse of "development takes time" is slowly vanishing. And it's becoming obvious that the real bottleneck always was understading and communicating what needed to be built.

## IESIE: A Framework for AI-Driven Development

 Not so long ago, after a rushed week of development we had another of these "damn, this should be different" moments. And it felt like it was one too many, the straw that broke the camels back, something had to change. It's not that situations like that are extremely time-consuming (even though they can be), but it's the energy they drain. A two hour fix, can leave you sour for the rest of the day, because you know that it would be 0 hours if only it got mentioned just a couple of days back.

A software developer learns to expect and manage these type of situations so that they don't affect us as much, but the hard truth is that they are quite inefficient and very often unnessesary. Looking to solve this problem we created the IESIE Development Framework (pronounced like "easy" because that's what building products should feel like). It's a method for fast moving teams to effectively make medium to large product iterations from the initial spark of an idea all the way through to measuring it's impact in production.

IESIE breaks down the process of making software into five progressive stages, each building upon the last:

### 1. Ideation: A problem in need of a solution

You see a problem.. great! An opportunity to make things better! Every solution starts with a problem and an idea of how to solve it.
Problem show themselves through customers, business goals, or unique insights. It's not really important how the problem showed it'self what matters is understanding if, when, and how it should be solved.

The goal in this stage is exactly that. Identify a problem that is worth solving, and think about when/how it should be solved. You don't need to come up with every detail, in fact that would be counter-productive. In the Ideation stage we simply want to write down the rough idea for others to see. Note that rough does not mean vague, our communication should always be clear.

What we've seen working best is the following format:

- **Problem**: What is not working well?
- **Proposed solution**: What is the approch?
- **When**: When should we start?

For example:

- **Problem**: Our customers have difficulty finding products in our store because we lack search filters
- **Proposed solution**: Build filters in the product catalog. This would be common information users want to filter by (for example brand, price, year of manufacture) as well as a full-text search
- **When**: As soon as possible

Presenting ideas like that is simple and efficient, one can quickly write and read it, and it includes all the key information someone needs to understand what the project (product iteration) is about.

### 2. Exploration: Validating the idea

Now that the problem has been identified and written down. It's time to share it with the rest of the team so we can look deeper into it. This stage is all about exporing the problem while blending creativity and reason to improve the solution.
Creativity helps us expand the solution space by experimenting with better ways to solve the problem, it takes us from the unknown to exoloring what is possible. Reason on the other hand structures our options to refine and validate the solution, it takes us from the known to to finding the correct approach.

During this phase it's best to engage people with different perspectives and roles. For example **Business** people will help answer wether this initiative creates real value and if it align with where we're heading. **Product** will validate if this fits well with our current solutions, how to implement it, and wether users actually want this.
**Design** experiments with how the solution would look like, and how users would interact with it (in form of early mockups). Finally **Engineering** will identify the feasibility and effort required to build the solution, sometimes that can include early prototypes.

Exploration is not just about understanding the problem while expanding and refining the solution. It's also about validating wether building it makes sense. Not all ideas will make it out of the exploration stage, and that's completely fine, in fact that's great. Not all problems are worth solving. By exploring the idea in more depth you will either save yourself from solving a non-crutial problem or you go into solving it confidently knowing what to expect, it's a win-win either way.

### 3. Specification: Getting Things Clear

With the idea explored and validated it's time to specify how the solution looks like. The primary goal of this stage is cleary define the solution covering all key details and get everyone commited to that solution.

During the exploration stage we tried to understad the problem from various angles, probably not everyone arrived to the same conclusions or imagined the same solution. By writing a shared specification we can ensure that we all are on the same page and understands what we getting ourselves into. This way the whole team can commit to the same solution, minimizing surprises.

Now there is not one way to do this, depending on your team and project different types of documents might be the best fit. Some projects might require heavy design and UX modeling outlining every UI detail, others might be more technical, business or product oriented. You should always think about what is it that you are trying to achieve with this solution and use what works best for your team and project.

That being said there are some important questions the finished documents would be good to answer:

* Why are we doing this? (the business value)
* What exactly are we building? (how does the solution looks like)
* What is affected? (teams, systems, or processes involved)
* How does it work? (technical solution)
* How does it look? (user interface)
* How do we measure success? (metrics and KPIs)

To achieve this we'll have to get the whole team involved and possibly other stakeholders too.

- **Business** helps define key success metrics and goals
- **Product** writes detailed requirements with clear acceptance criteria
- **Design** creates comprehensive designs in Figma
- **Engineering** produces a technical design document outlining the solution approach
- **Project lead** breaks everything down into manageable tasks and tickets

But be ware, while multiple people will be contributing to the documention it's important not to overcomplicate things and get lost in a typhoon of docs. While it's important to deliver a comprehensive solution, it's even more important for it to be clear and easy to follow. That's why we recomend to create one main document that gives an overview and binds everything together, linking to the designs, technical details, and any other relevant information for the project. Additionally this document would also track the progress of the project like (status: planned/in progress/done), while also having an identifier so that future projects can reference to it. At Teacherspace we've been experiment with a doc optimized for IESIE, hopefully I'll find time to write about it soon.

An equally important part of the Specification stage is to create the individual tasks needed to complete the plan, this is your classical issues in the Task Management software of choice. The level of detail for these tasks heavily depends on each team, in highly autonomus teams you'd prefer a lean task description, while in others a more comprehensive one. Depending on your organization software development methodology you might want to also estimate your tasks or them into upcoming sprints. The idea here is to have the tasks ready so that when we enter the next stage we already know exactly what needs to be worked on and so that we can track the progress.

A thing to note here is that even though we'll have a comprehensive plan, we should still allow for some flexibility, there are cases where we learn new information later on when we have already started the implementation of the project. Even though that's the exact situation we try to avoid with IESIE, we can never be perfect, some things might slip through the cracks and that's ok. But when this happens we should make sure that we update our documentation so that the plan still reflects the completed outcome. This can be done changing the source or by adding Addendums at the end.

As the last step in this stage we need to ensure that everyone is aligned and argees on the project plan before moving forward. This can be done async, however we found that a short 30-45 minute meeting with key stakeholders works the best. We don't expect everyone to have understood every detail of the plan, as for example a business person might find it unnessesary to make sense of the technical implementation. That's why we recomend a main document, it's to provide the "glue" making sure we that we are all aligned on the high level concerns. By the end we should feel confident that we know what we are getting into and that we are ready to move forward with it.

We often find this stage to be the most challenging, this is because we are involving multiple stakeholders, but also because of the difficulty in understanding exactly what needs build and how. As AI agents are becoming increasingly more effective on executing plans, so does the importance of creating comprehensive and well thought plans, becoming better at this skill is crutial to make the most of the future to come. I will be sharing more about what I've learned trying to make the most of AI assisted development, so stay tuned if you find this interesting. But not to get ahead of ourselves let's go to the next stage **Implementation**.

### 4. Implementation: Solving the problem

We have a plan, time to make it a reality! By now everyone should be aligned while also having a good understanding of the problem and how to solve it well.
Usually we think of this part as "the real work", writing code, configuring systems, essentialy bringing the idea to life. But what we find is that when we've already done the previous steps, implementation becomes surprisingly smooth.
Suddently the need for excessive coordination while working on tasks becomes minimal, developers can focus on the work without needing to go back and clarify details, which also frees up the rest of the team so that they can focus on what's coming next, new ideas, exploring other projects, making the next set of specifications, or even evaluating what's been shipped.

Since we've planned the tasks the development team can work through them in sprints or kanban style, handling all the usual suspects as:

- Setting up infrastructure
- Writing and reviewing code
- Coordinating with external services or partners
- Adding product and business metrics
- Addresing performance and security concerns
- Product QA
- Finally, releasing to staging and production

It's important during this step not to forget that we already have a well specified plan. While initially it served for us to get a better understanding what we need to build and get everyone aligned, it can also be used to speed up the development by using coding agents. There is a lot to say here, from learning to write agent leaning specs, using MCPs to connect coding agents with services like Figma and Linear, writing PRPs in tasks so that they can be fed straight to agents, all the way to creating specific agent workflows that integrate with the specification documents and the IESIE methodology directly. It's definetely something we could delve deeper in, but this article is already getting long. So off we go.

By the end of this stage you'll have live, working software in your customers hands. Most plans usually stop here, after all, the problem is now solved right? Not with IESIE, we have one last crutial step, evalutation.

### 5. Evaluation: Closing the Loop

Since the popular book Measure What Matters by John Doerr was published, we have seen an increase in interest for measuring success using KPIs (Key Performance Indicators) and having OKRs (Objectives and Key Results) even in smaller companies like startups. And for a good reason, businesses that measure their outcome often seem to do better. They solve more problems for their customers and have better knowledge of where they stand in the market. Measuring success is key for knowing what to focus on next. But that's where most development frameworks fall short, they ship and forget, evaluating the success of a project is rarely accounted for in the initial plan, and if so it is a nice to have that hardly ever sees the light of day. This results in organizations often making sub-optimal or uninformed decitions, and spending resources ineffictively.

And that is why we believe evaluation should be part of every project. During exploration and specification we should have already identified how to measure the success and quality of the project, these can be product metrics like feature usage, user satisfaction, session frequency etc. Business metrics like measuring the efficiency of a process (for example shipping more packages per hour) or even technical for example how long it takes to load a page. These metrics are then gathered automatically in the product during the Implementation phase, or we have defined how they should be measured otherwise.

Alright, so we've shipped the project, now before moving on we want to analyze the effect it had on our business and product. We do this by looking at the metrics we defined and seeing wether they matched our expectations, did we expect that the new export feature is going to be used by 30% of active users around 3 times a week and instead we see it used only by 10% 2 times a week, why is that? Did we not communicate the feature well, was it not as helpful as we initially thought? Is is cumbersome to use? Maybe the export quality is not what they expected.

We don't just look at the data once, but follow the trends, usually the evaluation can last weeks to months after the project is done. We won't be spending the whole day on it, but rather do a check in to understand if our expectations are matching reality or notice interesting patters. Maybe we find out that users tend to use a feature 1-2 times before not interacting with it again, that likely shows that they have interest in it but their expectations were different. Or we see that initially they don't use it but over time they use it more and more, which might hint that it requires some getting used to, maybe some better documentation or onboarding will help.

The evaluation stage is all about making the best out of the decitions we've made using measurable results. But it can also provide some buffer time for post-release adjustments. Knowing that a project is not done right after releasing it gives the management team the space they need to make sure it's in the best shape it can be. The important thing is that we also gather feedback from actual users. Sometimes a feature that seemed perfect in our heads falls short in reality. Maybe the UI needs a bit of teaking, or we see that we need to improve the performance, or we realize that doing X is only valuable if users can also do Y.

Finally this last step also can bring new insights for future projects. By taking a step back and looking at what we have done we are opening ourselves to new ideas about of what else can be done. This creates a cycle where the Evaluation step results in new ideas starting the IESIE process all over with new projects.

## Why This Isn't Waterfall 2.0

You might be skeptical of this approach, the industry has been burned with the long and inflexible processies of the Waterfall approach where a detailed specification preceeds development, and this seems earingly similar, are we revisiting old mistakes?

Well no. There's a crucial difference! IESIE is built for small, fast-moving teams where everyone collaborates throughout the process. Instead of requirements flowing top down, we have the whole team contributing. Developers, designers, product folks, anyone can bring ideas with Ideation and everyone needs to work together during Exploration and Specification.

Furthermore we are talking about bite-sized projects here. These product iterations should be completed in a few weeks not months, and we would never expect something taking the year-long death marches of traditional waterfall. The final thing to understand is that IESIE is made for **product iterations** not grand projects starting from 0, instead of making a risky and ambitious prediction of the future we are instead evolving a living product little by little.

Most importantly, IESIE is designed for our new reality where AI assistants can turn a good specification into working code in minutes. The bottleneck has shifted from the difficulty to solve technical problems to the ability to make sense of problems and communicating the solution clearly.

## The Beautiful Cycle

What makes IESIE particularly powerful is its cyclical nature. The evaluation stage doesn't just close out a project, it gives the space for reflection so one can see new problems to be solved. You might discover that users are trying to use your feature in unexpected ways, or that solving one problem revealed some new more interesting ones. These insights flow right back into ideation, and the cycle begins anew.

This creates an everlasting rhythm of innovation. Each solution gives an opening to look again into our system and identify if it's solving the problems it should.

## Does It Actually Work?

Yes, at Teacherspace, we've started using IESIE for most projects, and it's been quite helpful. It streamlined the communication process, making it easier to evaluate ideas and validate them before committing resources. And as a developer I am happier because we've reduced the times we had to deal with shifting requirements (the inital goal was a success!!!). Overall it feel like the the whole org is now more confident when we take decitions.

Are we perfect at it? Not even close. We're still figuring out how to make evaluation more systematic and define better metrics, and sometimes we catch ourselves trying to skip steps when we're excited about an idea. But that's the beauty of a methodology, it's something one needs to learn how to use effectively over time. There is always something to be improved, especially something new as this.

## What Do You Think?

Using the IESIE framework has been effective for us, but I'm under no illusion that it's the perfect solution for everyone. Every team has different challenges, different dynamics, and different needs. What works for us might need tweaking for you, or it might not work at all.

If it's something you'd like to take up, it might need some time to get used to, start small, maybe picking just 1-2 smaller product iterations to to test out the waters and familiarize the team with it. And remember to be patient new things take time to get used to, especially when they are practices to be shared across the whole team.

I feel like this approach is the best one I've worked with so far, but I'd love to hear what others think of it. Does it resonate with challenges you're facing? Have you tried something similar? What's worked (or hasn't) for your team when managing the chaos of startup development?

Maybe your team has already solved these problems in a completely different way. If so, please do share in the comments.

Software development has been rapidly advancing and with the advent of LLMs and coding agents I feel we are quickly approaching a new era of software development. I am really excited for this future and would love to write more about how to make the best of it. Even though I have a busy schedule I'd love to find the time and to write one article every 2-3 weeks, and publish it here, next I want to delve deeper on the Specification stage of IESIE since it's a really important one and there can be a lot of depth to it, at Teacherspace we've been experimenting with a new type of document specifically designed for this methodology so I am looking forward to share more about it!

Anyhow thank you for taking the time to read though this whole article, I hope it helps you manage the chaos of your own fast-paced team.
