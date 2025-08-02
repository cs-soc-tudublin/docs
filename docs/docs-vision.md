---
title: CS++'s Approach to Docs
created: 2025-08-02T23:05:05
modified: 2025-08-02T23:50:26
tags:
   - meta
---

# **DOCS** - Our Philosophy

!!! info "Rant warning!"

	This page is more a manifesto about writing documentation instead of actual documentation on how CS++ operates. Don't be radicalised!

In tech, documentation is at the core of building a stable and reproducible system that can be restored, expanded and maintained by a totally new set of people than the original creators.

In a worst case scenario, if the society was mothballed for a few years and all that was there was the hardware in the rack and none of the original sysadmin, the new generation should be able to use these docs to bring the servers back, and understand how and why they're doing each step.

This is commonly called the 'hit by a bus philosophy'

## Heavy Vehicle Road Traffic Incidents

The [Bus Factor](https://en.wikipedia.org/wiki/Bus_factor) is a risk model that boils down to '*What if this person wasn't here anymore?*' and aims to identify critical people or bits of knowledge that have not been shared, with the purpose of sharing this information.

The best way to share information is to tell others, and one of the best ways to do this when in a society or working on systems with lots of moving parts is documentation.

## Do We Need to Care about Heavy Vehicle Road Traffic Incidents?

CS++ has at least one recorded case of dying and being revived, and this leading to  loss of technical information.

CS++ was restored in March of 2022, dying in ~2020 as 'Comp Soc'. At that time, the society had multiple server (About 12) in their own server room in Aungier Street.

When the society was restored, no-one knew the room or even the hardware existed, and now it's become our server room!

## Looking Both Ways

In Societies, the average turnover is about four years. That is a brand new committee every four years, and that's not a long time!

This makes it hard to do long-term planing, and instead Societies grow through incremental improvements and proper handover.

For CS++, where we run mission critical software not just for us but for others, it is just as important if not more to write and update the documentation and train the successors! You do not want a single point of failure that when a sysadmin graduates, the ability to securely network servers is lost forever.

Writing docs is part of the obligations of sysadmins, updating them as hardware, services, and procedures change.

In a perfect world, all of the current sysadmins could be hit by a bus, and the replacement sysadmins would be able to use these docs (And private docs stored internally) to find the Server Room, get access and both learn and rebuild the entire technical stack from scratch.

## Brick by Brick

These docs are organised in Layers (like onions!). Each layer builds upon eachother. Starting on the hardware that runs the show, and ending on how to make your life easier when maintaining a cluster.

You can't automate tasks when you don't have tasks to do. You have no tasks without having services. You have no services without an Operating System. You have no Operating System without Hardware.

And you cannot understand any portion of that unless you also understand what it's built on.

These docs start at a very simple level, with [**LAYER ZERO** - Hardware](./zero/index.md), explaining the concepts behind servers & networking at a First-Year level without assuming prior knowledge.

Each layer builds atop eachother until the whole stack is known and understood.

So, from nothing, you should be able to pass the 'First Year test', and give an average First Year student these docs, a broken system, and they should be able to understand them and fix what does not work.

## Inertia and Interest

Writing docs takes a long time, and writing docs of this scale is even harder.

Once the majority of docs are written, there remains inertia to keep them up-to-date. Without updates as things change, the docs begin to drift from what is canon, and can lead maintainers down the wrong paths.

Docs are the most holy runbook, and also the most verbose! So making the edits as things change allows your legacy and work to remain within the society.
