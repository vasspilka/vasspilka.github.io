---
layout: post
title: "The journey of MicroWords PT2"
date: "2021-05-10 20:43:21 +0200"
---

## Recap

In part one of the series we explored what is MicroWords about and started building it, we looked at some attributes of eventsourcing and how we can use events and aggregates to model an application. In this part we will continue modeling the core of our application.
We will start by creating locations which can be used as places to put content into as well as move around. Then we want to look further into action and how to use metaprogramming to help us define them in a dynamic but structured way. Finally we will create a full ruleset from which we will create our first world.

## Creating Space

We can think of space as the sum of locations existing in a given system. So in order to support space we need a way to structure locations, one way to represent them could be lists of integers, for example by having lists each containing two elements (`[1, 1]`, `[1, 2]`, `[2, 1]`) we can represent locations existing in a two dimensional space. Theoretically the integers could be infinetely big, allowing us to create an infite two dimensional space, however it would make sense for us to set some limits in order to make the space more managable which would improve content discoverability in addition to making the space less resource heavy. For our first world lets settle with an 500x500 grid of possible locations. For each location that can possibly exist in a world we need a unique identification in order to be able to refer to it, we can create such an identifier by creating a string containing of the world name and the location coordinates for example if we have a world named `"europe1"` and the location `[50, 63]` we could create the string `europe1:50,63` as a unique identifier for that location. This will allow us to refer to any location easily given we know the coordinates and the world name. This is important because we will be using this identifiers everytime we need to see or interact with a location.

Now that we have discussed how to create locations in theory, let's see how we can use a commanded aggregate to do so in practice.

## Improving our rulesets by action definitions

When we build our minimal ruleset in the previous article we created a module and defined some callbacks that would get called by our aggregates to build the actions and transform the state of the explorer. Now that we have locations we will also need to define how locations are affected by actions, furthermore we need to make sure that we are doing that in a scalable way. First lets see enrich our ruleset by create two actions, one to create notes and one to place them to locations. The reason we want to separate these actions is simple but not obvious, each location can only hold up to one artefact, and in an open world people would compete to put their content on a location, if the actions where not separate a situation could easily arise where an explorer would start typing in a note only to figure out the location has already been filled while they where typing it, this would end up being frustrating. So instead we will be separating the two actions explorers will be able to create their content and store it in an inventory, then whenever they see fit they can place it into a location. This will not eliminate racing conditions between exploreres when placing content however it will make it much less likely, and the cost of someone getting ahead of you will be minimal as they content will stay in your inventory. Furthermore by having an inventory we can allow for more types of actions, for example one can copy a piece of content putting it in their inventory to allow them to place it later

# World Agents
