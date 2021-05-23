---
layout: post
title: "The journey of MicroWords PT2"
date: "2021-05-10 20:43:21 +0200"
---

## Recap

In part one of the series we explored what is MicroWords about and started building it, we looked at some attributes of eventsourcing and how we can use events and aggregates to model an application. In this part we will continue modeling the core of our application.
We will start by creating locations which can be used as places to put content into as well as move around. Then we want to look further into action and how to use metaprogramming to help us define them in a dynamic but structured way. Finally we will create a full ruleset from which we will create our first world.

## Creating Space

We can think of space as the sum of locations existing in a given system.

Locations can be represented as lists of integers, for example by having lists each containing two elements (`[1, 1]`, `[1, 2]`, `[2, 1]`) we can represent locations existing in a two dimensional space. Theoretically we can create any amount of dimensions and allow for infinite size

e. we can theoretically model an infinite amount of locations inside a two dimensional space. For our first world we can limit that space to help with discoverability, let's settle with an 500x500 grid of locations. This means that any location can be identified by a list as .t.c

# Ruleset trouble

# World Agents

# Actions

# Type definitions
