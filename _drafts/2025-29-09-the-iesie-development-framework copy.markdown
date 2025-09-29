---
layout: post
title: "The IESIE Development Framework"
date: "2025-09-27 20:43:21 +0200"
---

Have worked mostly with startups where:

* Constantly new ideas
* Chaotic environment with high uncertainty
* Need for fast iteration

The main bottleneck usually was not building the product but rather forming good ideas and specifying them.
Often facing the problem of requirements changing during the development process, but not due to evolving business goals, rather the inital idea was not well explored and specified.


Startups often jump from exploration to implemetation without properly specifying the problem or and it's solution. This drains developers as well as other people involved in the process.

I was faceing the same issue in my current startup Teacherspace, however this time the bottleneck was even more apparent because AI code-agents can make development so much faster if it's well specified.

Pondering on this issue I developed the the IESIE Development framework (rhymes with Easy). It's a framework to progresively move small product iterations called Projects (units of work that take 1-4 sprints usually) from an idea all the way to production and beyond.

IESIE has 5 stages that need to be completed progresively one after another


* Ideation
  Purpose: Generate and capture raw ideas.
  - Beginning of the process
  - Rough and uncertain
  - Only 1-2 people
  - A team member proposes a new concept (feature, improvement, or product).
  - The idea is briefly documented in a simple format (one-pager, card, or project note).
  - Key elements at this stage:
    - Problem statement: what problem this addresses.
    - High-level solution: rough outline of how it might work.
    - Why now: reasoning for pursuing the idea.
  Output: a clearly communicated idea ready for further exploration.

* Exploration
  Purpose: Assess feasibility and alignment.    
  - The broader team engages with the idea to refine it.
  - Different perspectives are applied:
  - Business: does this create value? Does it align with strategy?
  - Product: is this meaningful to users? How will it impact experience?
    - Usability checks.
  - Technical: is this feasible with current infrastructure?
    - Prototype spikes
  - Design: how could this be realized from a UX/UI perspective?
    - Early Mockups
  - Risks, dependencies, and potential alternatives are surfaced.
  Output: a validated concept with enough confidence to proceed to detailed planning.
* Specification
  Purpose: Define and structure the work.
  - The idea is transformed into a detailed project specification.
  - Dependencies identified and documented.
  - Success metrics defined (what will we measure post-release).
  - Deliverables at this stage:
    - Product: A detailed project document with acceptance criteria. PRP
    - Design: detailed designs in Figma 
    - Technical: TDD with solution for the problem
    - Product/Eng manager or lead: Breakdown into tasks (user stories, tickets, subtasks).
  - Finally the team has to align and agree on the complete specification (this does not mean that it can't change, or that absolutely every tiny detail is specified, rather we are minimizing miscommunication and uncertainty)
  - Different projects might need different deliverables, for example a small tech-debt project, might only have a TDD and tasks, but a new product feature with UI will likely need everything
  - Specifying measurable success metrics is important at this stage
  Output: Detailed project doc, Figma desigs, Linear tasks with well written specifications a structured backlog ready for implementation.

* Implementation
  Purpose: Deliver the solution.
  - Execution of tasks in sprints or iterations.
  - For software projects these activities may include:
    - Writing code.
    - Configuring infrastructure.
    - Coordinating with external partners or platforms (managing integrations, communate with software partners etc, creating accounts)
    - Testing and QA before release
    - Performance, scalability, or security validation (if relevant).
    - Releasing the feature
  Output: A functioning product or feature that matches the defined specification.

* Evaluation
  Purpose: Ensuring the quality of the project and assessing it's effectiness.
  - The implementation is validated against specifications and success metrics.
  - Buffer time is given for post-release improvements & fixes
  - Feedback from customers/users is gathered
  - Post-implementation review: did we deliver the intended value? what can still be improved?
Output: Not nessesary, but may be a report on the impact of the feature including success metrics


Initially one may confuse this with the infamous waterfall approach, however the aproach is very different. IESIE is designed for small teams that need to move fast, it works best when the whole team iterates together on exploring the idea and creating the requirements instead of a top down approach, all of development, design and product work together in exploration and specification to deliver the comprehensive requirements that will be implemented. Additionally the projects should be small products segments that overall don't take longer than 2 months from ideation to completion, sometimes they can be completed in just 2 weeks, never years. 

IESIE is agile optimized for the world of AI assisted programming were having specification takes center stage as a well specified task can be coded up by agents in minutes. 

It helps fast moving startups to move their plentifyl ideas down an effective pipeline. Keeping everyone alined and most importantly avoiding the energy draining cases where due to poor communication or alignment a completed task needs to be changed. Most importantly it's a ciclical approach, from the last Evaluation step you should start seeing important info that will give you new Ideas so you can start over the cycle for new projects

So does it work? Yes! In teacherspace we have been using this framework for the past few projects and it has helped us keep organized and significantly reduce unexpected surprises that usually dragged us down. To be honest are still learning to work with this new framework and there is lot of room to improve, especially in the last step Evaluation but it's definetely something we'll keep on doing