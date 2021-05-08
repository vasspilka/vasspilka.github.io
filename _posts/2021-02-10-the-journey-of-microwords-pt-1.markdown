---
layout: post
title: "The journey of MicroWords PT1"
date: "2021-02-09 20:43:21 +0200"
---

## Introduction

For over a year on my spare time I have been occasionally working on a project I call MicroWords, lately I've been feeling that the core idea I had about the project started to solidify so I started with this article to draw some attention to it as well as further gather my thoughts. What I would like to share here is the journey and progress done so far as well as showcase some of the methods and tools I've used for it.

The project currently lives at [Github](https://github.com/vasspilka/micro_words) so be sure to check it out before or after reading this article.

So what is MicroWords, well the easiest way to put it would be it's a gamified content sharing platform. As a "character" you create and explore a world of content. One can think of it as a mix between minecraft and twitter. In truth however it's much more that that, you see the concept came as an offspring to some experiments I wanted to do with natural selection, I wanted to create a platform where agents with energy react to actions done by a user, these actions would drive an energy economy that determines what survives or not, good agents would reproduce and it would be more likely to encounter them again.
My initial thought experiments where around a concept of an article curator, where the agents would choose articles from the web to serve to you based on criteria like topic, length, source etc then your actions would "feed" these agents or punish them, with time the agents that fit your preferences would survive and the others would perish resulting in better article curation for the user.

## Enter Microwords

While the project was initially inspired by the forementioned idea, it has since parted and evolved into a project of it's own and is turning out very different. It is still early to say what exactly this project is evolving to, however I am starting to see a lot of potential in it. In today's world, social media and content platform mostly attempt to grab ones attention with flashy titles of viral and clickbaity content, discoverability and explorations have somewhat been lost in todays web. I see Microwords as a way to bringing back some of the joy of exploration and discoverability, a place where people can collaborate/compete and build "worlds" of content together in novel and fun ways. But I feel we are getting ahead of ourselves and it's still not clear what Microwords is even about and more importantly what is it we need to build, so next up lets focus on the requirements.

## Requirement

As we mentioned our project is a content sharing platform, but what I truly wanted it to be is a framework to build all sorts of types of content sharing platforms, this is very important as different people have different ways they like to experience the discovery and sharing of content. In order to achieve that we need a system with flexibility built in, we can do so by defining rules of how one can interact and discover content. In our system this will be done with actions and a concept of a ruleset. Furthermore what we want is different communities being able to come together we want places for broad or narrow topics, that can be private or public, for this we will use a concept of a world, in which content and users exist. These worlds might share the same rules, but they will be completely isolated, in software terminology one could think of them as tenants. And then of-couse we must have the content itself, for starters I will be building Microwords to only support small to medium text, similar to twitter, however my goal is to support any type of content in the future as photos, videos, articles and whatever else one's heart desires. Finally it should be open-source and available for anyone to extend and integrate on their own terms.
These are our core requirements to make this happen, there are other features that could make these platform richer and more fun, but we already got a bunch here so let's get us started.

Being a fool for the Elixir programming language it is a no-brainer for me that it should be the choice for this project, furthermore the past few years I have been fascinated with event-sourcing and Domain Driven Design and believe it can give good foundations for this project, so using the Commanded library we will leverage this type of architecture to build a very interesting project!

## Starting the project

Before we begin with the project I want to take a moment to show my appreciation for Opensource and how it makes all this possible. I would especially like to thank the contributors of Erlang, Elixir, Phoenix and Commanded as those are the tools that we are predominantly going to use here, however open-source is a very intertwined phenomenon, and in my opinion it shows how amazing humanity can be, so thank you all. 

Now with no further ado let's get started with the project. Since we are using phoenix as the web-framework, we can start by generating our project with the elixir's `mix` tool. We will also be using liveview so we need to run the following command to generate our new project.

```
mix phx.new --live micro_words
```

As mentioned this will be an event-sourced system, so now that we have our project generated let's add the dependencies we'll need for that.
Furthermore even though elixir is not strongly typed, I would like to use something that will help us give structure and specify better our domain, for that we can use a library called `typed_struct` among with `dialixyr` they will help us with type checks.
So lets add those dependencies to our `mix.exs`.
```
{:commanded, "~> 1.2.0"},
{:commanded_eventstore_adapter, "~> 1.2.0"},
{:eventstore, "~> 1.2.0"},
{:typed_struct, "~> 0.2.1"},
{:dialyxir, "~> 1.0", only: :dev, runtime: false},
```

The first things we want to do now that we have our project set-up is to start thinking about the domain, in event-sourced applications this is done by thinking about events and aggregates. Events are incidents that happen in our system, while aggregates are entities that combine a set of information or concepts together. In different types of systems these concepts are modelled in different ways. We are using `commanded` to help us handle the event-sourcing part and since it's quite opinionated in how these concepts are used, for us aggregates will be entities holding information that accept commands and emit events.

## Structuring the model

In our requirements we mentioned, users, actions, worlds, rulesets, and content not all of these are going to end up being aggregates. So let's start by modeling our events to get a better understanding of what should end up being an aggregate.

Ok, we know that we want different types of worlds, each having a ruleset (rulesets can be reused) so lets define a `WorldCreated` event, then we want an event for users to enter these worlds `UserEnteredWorld` these users can take actions `UserActionTaken` and we also need a way to affect the users `UserAffected`. For rulesets we will use elixir modules with an expected interface, so creating and changing them will be outside our event-sourced domain, now how about content, we might be thinking we need a `ContentCreated` event, however we would like this platform to be flexible, and creating events like this would make it harder for us, we then might need a `ContentEdited`, `ContentLinked`, `ContentXXX`, you get the drill, this would not be very flexible, instead we can leverage the `UserActionTaken` event to do all of these and define the rules of what will happen with our rulesets.
These generic events would not be adviseable for applications with different domains, generalized events are harder to work with and to reason about, however the nature of our application is to be generic and multipurpose that is the reason why we can get away with it. In essense the domain in this case is generalization.
Now lets look at next big piece. Actions, by the looks of it they will play a big role in our application, for this reason we need a way to be able to provide a strong definition for them but at the same time keep them flexible as we evolve what microwords is. A well defined structure is exactly what `typed_struct` can provide for us, so let's define the action as a typed struct.

So given these assumptions lets create our first modules to hold these definitions. Because I wanted to spice things up a bit, I decided to call users as explorers and content as artefacts. This will only affect how we call these resources, but I felt it was more in line with what we are trying to build.

In our actions module, for starters we will only add as attributes it's type that will be an atom (like `:post_created`), the ruleset it belongs to, it's cost and the ids of the other entities.

```elixir
defmodule MicroWords.Action do
  use TypedStruct

  @derive Jason.Encoder
  typedstruct do
    field :type, atom()
    field :ruleset, module()
    field :explorer_id, binary()
    field :artefact_id, binary()
    field :cost, integer(), default: 0
  end
end
```

And for our events we'll define them as so

```elixir
defmodule MicroWords.Events do
  use TypedStruct

  typedstruct module: WorldCreated do
    @derive Jason.Encoder
    @moduledoc """
    A new world was created.
    """

    field :name, binary()
    field :ruleset, module()
  end

  typedstruct module: ExplorerEnteredWorld do
    @derive Jason.Encoder
    @moduledoc """
    Explorer with `id` entered world.
    """

    field :id, binary()
    field :world, binary()
    field :ruleset, module()
  end

  typedstruct module: ExplorerActionTaken do
    @derive Jason.Encoder
    @moduledoc """
    Explorer has taken an action.
    """

    field :id, binary(), enforce: true
    field :action, MicroWords.Action.t(), enforce: true
  end

  typedstruct module: ExplorerAffected do
    @derive Jason.Encoder
    @moduledoc """
    Explorer was affected by action.

    Not all actions create a user affected event.
    """
    field :id, binary(), enforce: true
    field :action, MicroWords.Action.t(), enforce: true
  end
end
```

Nice, we now have our action and first set of events defined. It is now time to talk a bit about commanded, running event-sourced systems usually comes with some overhead, depending on the needs there might be a lot of abstractions that must be build, commanded takes an opinionated but quite generic approach to provide these abstraction for elixir programs, similar to phoenix it does a lot of things for you without seemingly getting in the way, as long as these abstractions fit our needs it will save us a lot of time, effort and complexity.
If you are interested more about ES in elixir you should definitely check [commanded on github](https://github.com/commanded/commanded) as we will not be going in depth here.

In micro-words we are using commanded to handle our command dispatch, aggregate state, and the insertion of our events, furthermore we use a form of event-handler called process-managers, they enable us to create a chain of events that involve different aggregates.

Having talked a bit about the abstractions we are going to use lets create our first aggregate, the explorer.

```elixir
defmodule MicroWords.Explorers.Explorer do
  use TypedStruct

  alias MicroWords.Explorers.Explorer

  alias MicroWords.Commands.{
    EnterWorld,
    TakeAction,
    AffectExplorer
  }

  alias MicroWords.Events.{
    ExplorerEnteredWorld,
    ExplorerActionTaken,
    ExplorerAffected
  }

  typedstruct do
    field :id, binary()
    field :world, binary(), enforce: true
    field :ruleset, module()
    field :energy, integer()
  end

  def execute(%Explorer{id: nil}, %EnterWorld{} = cmd) do
    %ExplorerEnteredWorld{
      id: cmd.id,
      world: cmd.world,
      ruleset: cmd.ruleset,
      energy: 0
    }
  end

  def execute(%Explorer{id: id} = state, %TakeAction{id: id} = cmd) do
    %ExplorerActionTaken{
      id: id,
      action: state.ruleset.build_action(state, cmd.type, cmd.data)
    }
  end

  def execute(%Explorer{id: id}, %AffectExplorer{id: id} = cmd) do
    %ExplorerAffected{
      id: id,
      action: cmd.action
    }
  end

  def apply(%Explorer{}, %ExplorerEnteredWorld{} = evt) do
    %Explorer{id: evt.id, world: evt.world, ruleset: evt.ruleset}
  end

  def apply(%Explorer{} = state, %ExplorerActionTaken{} = evt) do
    state.ruleset.apply(state, evt)
  end

  def apply(%Explorer{} = state, %ExplorerAffected{} = evt) do
    state.ruleset.apply(state, evt)
  end
end
```

With a keen eye we can notice a couple of things here, we see a pattern of defined functions, `execute/2` and `apply/2` seem to be receiving as first argument an explorer structure and as second argument either a command or an event. Furthermore `execute/2` seems to be returning event structures while `apply/2` returns an explorer structure, that is where we can notice the next thing, we are using a parameter attribute to call a function. The apply and execute functions can be explained by how commanded expects an aggregate to be modelled, while we have not explicitly defined that this module uses an interface expected by commanded it actually does. Commanded will use this module to create agents that will hold our aggregate state, receive commands and emit events. We can rely on commanded that the aggregate state will always be up to date and will only ever process one command at a time, so no race conditions can happen.

Now what about these unusual function calls like `state.ruleset.apply(state, evt)` and `state.ruleset.build_action(state, cmd.type, cmd.data)`? In our requirements we expressed that we want a flexible way to define functionality and we called it rulesets. These rulesets will be modules that help us define different types of rules. Let's get started by writing our first ruleset definitions.

```elixir
defmodule MicroWords.Rulesets.Basic do
  alias MicroWords.Explorers.Explorer
  alias MicroWords.Action

  alias MicroWords.Events.{
    ExplorerActionTaken
  }
  
  def build_action(%Explorer{} = entity, :sleep, _) do
    %Action{
      type: sleep,
      ruleset: __MODULE__,
      explorer_id: entity.id
    }
  end

  def apply(%Explorer{} = entity, %ExplorerActionTaken{action: %{type: :sleep}}) do
    %Explorer{entity | energy: entity.energy + 20}
  end
end
```

While this action requirement is pretty simple it helps us understand what it takes to build different types of actions. Obviously this way is not scalable and the actions are not easily reusable. There are better ways, we will revisit rulesets to make them more dynamic and reliable, however for now simple modules and functions will do.

Alright with Actions, Explorers and Rulesets being handled let's now move to the worlds and content. This is where I started encountering my first hickups, the content (artefacts) needed to exist within a world, at least conceptually. Furthermore we know that the content will be the most accessed and manipulated resource, and that the users will not want to get the content randomly but rather in a structured way. Finally we want the way content is accessed to be flexible by using our rulesets. My first thoughts where to create an artefact aggregate, however that posed the problem of agency. It is important for us to know what artefacts one has access to within a world, so we need some type of agent that tracks that, and keep everything up to date. That would be hard to do having independent agents for each artefact, by CQRS standards we could create a read model and query it, however then we would introduce eventual consistency concerns and there would an overhead orchestrating it all, as we scale we will have to eventually create a read model, but let's try to defer it as long as possible. Using the world it'self as the aggregate containing all the artefacts could solve these issues, but only at the cost of introducing new ones. Having a single agent to handle all actions happening within it could easily make it a congestion point, in a scenario where there are thousands of explorers a world would be fludded with incoming/outgoing messages and at peak times would slow everybody down. We could make the load on that agent a bit smaller by creating replicas for reading and downstream subscriptions but but not without reintroduce the eventual consistency issues.

This issue troubled me, the solution I had in mind was to create a FIFO list that would act as a stream. I could push artefacts to it and subscribers would pick items from it, it was hard to implement and furthermore I was realizing that it would have various problems, updating the items already on the list would be an expensive operation. The longer I tried to make it work the more it looked like a bad idea.

After a lot of mental struggle it was clear that this was not the correct approach... That is when a new idea presented to me. What if our worlds would have some space inside them in which we could place artefacts, the explorers could move around and explore the space inside a world and if a given position was empty they could place a new artefact otherwise they could interact with the artefacts that was placed there. This idea solved a lot of technical problems for me, but more importantly it brought this new fun aspect to Microwords, now it felt more like a physical place, one which can be explored rather it being a feed to scroll through. Of-course this poses other UI requirements for example if we model a two dimensional space we need to move north, east, south and west, so in order to find content a user would have to use arrow or "wasd" keys, this would not necessarily be bad and it could actually be nice for the user, they could learn in which areas certain type of content tends to be and explore areas around there, then maybe they can go to other areas to see what is there, since there would be locations people could collaborate and build regions of content. But we are not confined to two dimensions, in theory we could create a one dimensional space and explorers could jump from location to location randomly, or alternatively build a world with seven dimensions to achieve a similar way to move semi-randomly by always increasing or decreasing a single unit in a random dimension, these multidimensional spaces might sound complex but in reality they would not need to be so hard to implement.

In our next article in the series we are going to create the concept of a world and locations, then we will further develop our application so that we can move around in a two dimensional space and see artefacts.
