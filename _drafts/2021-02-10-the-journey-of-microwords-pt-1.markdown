---
layout: post
title: "The journey of MicroWords"
date: "2021-02-09 20:43:21 +0200"
---

# Introduction

I started this article to ..

In this article we will be covering the journey and progress of how the MicroWords project is build. And in doing so I would like to share some of the challenges and *eurica moments* I had among the way. 

So what is MicroWords, well the easiest way to put it would be it's a gamified content sharing platform. As a "character" you create and explore a world of content. One can think of it as a mix between minecraft and twitter. However in truth it's much more that that, you see the concept came as an offspring to some experiments I wanted to do with natural selection, I wanted to create a platform where you have agents with energy that react to actions done by a user, these actions would drive an energy economy that determines what survives or not.
Initially the concept was around an article curator, where the agents would chose articles from the web to serve to you based on criteria like article topic, length, source etc then your actions would "feed" these agents or punish them, with time the agents that fit your preferences would survive and the others would perish resulting in better result for the user.

## Enter Microwords

While the project was initially inspired by the forementioned idea, it has since parted and evolved into a project of it's own and is turning out very different. It is still early to say what exactly this project is evolving to, however I am starting to see a lot of potential in it. In a world of mass social media where information is processed and predigested for you, I see Microwords bringing back the joy of exploration and discoverability, a place
where people can collaborate and build "worlds" of content together, instead of competing for user attention with short lived and viral/click-baity pieces. In that place the content and the experience of getting to it is fun and nourishing.
But I feel we are getting ahead of ourselves and it's still not clear what Microwords is even about and more importantly what is it we need to build it so next up lets focus on the requirements.

## Requirement

As we mentioned our project is a content sharing platfrom, but what I did not mention is that what I truly wanted this to be is a platform to build all sorts of types of content sharing platforms, this is very important as different people have different ways they like to experience the discovery and sharing of content. In order to achieve that we need a system that is flexible in defining rules of how one can interact and discover content. In our system this will be done with actions and a concept of rulesets. Furthermore what we want is different communities being able to come together we want places for broad or narrow topics, that can be private or public, for this we will use a concept of a world, in which content and users exist. These worlds might share the same rules one can discover and interact with the contect, but they will be completely isolated in software terminology one could think of them as tenants. And then ofcouse we must have the content itself, for starters I will be building Microwords to only support small to medium text, similar to twitter, however my goal is to support any type of content in the future as photos, videos, articles and whatever else one's heart desires.
These are our core requirements to make this happen, there are other features that could make these platform richer and more fun, but we already got a buch here so let's get us started.

Naturally it being a content sharing platform this will be a web project, I myself being a fool for the Elixir programming language it is a no-brainer for me that it will be the choice for this project, furthermore the past few years I have been fascinated with event sourcing and Domain Driven Design and I feel like it could be a good fit for this project, so using the Commanded library we will leverage this type of architecture to build a very interesting project!

## Starting the project







---------------------

# Requirements

# First breaktrhough (dimensions)

# Ruleset trouble

# Actions

# Type definitions

