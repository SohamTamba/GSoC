---
layout: post
title:  "Application Period"
date:   2018-05-26 14:10:51 +0800
categories: GSoC
tags: Project
description: Choose a Project, Made Contributions, Wrote a Proposal, Got Accepted.
---


**Application Period:** 12<sup>th</sup> Feb to 27<sup>th</sup> March 2018.

# Introduction

GSoC (Google Summer of Code) is a program in which, students provide open source organizations with a proposal that suggests improvements to their software. If accepted, the student will spend 3 months implementing (coding) their proposal, while being advised by a mentor from the organization. I would break up my activities during this time as:

1. Choose a mentor organization and project.
2. Interact with the community and contribute.
3. Write a proposal.
4. Find a committed mentor.

# Choosing a Project
Firstly, prospective applicants must choose a mentor organization from the list published in the [GSoC website](https://summerofcode.withgoogle.com/). On 12<sup>th</sup> February, the finalized list of mentor organizations for 2018 was published.

I was interested in a `HPC` (High Performance Computing) project. I had previously come across `Julia` while skimming through the profiles of professors and graduate students and thought I would likely find a suitable project. While going through the [Julia's HPC projects](https://julialang.org/soc/projects/hpc.html), I came across the `Parallel Graph Development` project which meant creating a parallel implementation of the graph functions present in [LightGraphs.jl](https://github.com/JuliaGraphs/LightGraphs.jl). 

I was already familiar with most of the algorithms implemented in the library, which lead me to believe I could make useful contributions to it. I literally chose the second project I explored.

# Contributing to LightGraphs
I spent the first month of the application period making contributions to LightGraphs.My [first contribution](https://github.com/JuliaGraphs/LightGraphs.jl/pull/839) is just one line that saved `(|E|-|V|+1)*(size of an edge)` memory in the implementation of Prim's Minimum Spanning Tree Algoirthm. Note that the PR (Pull Request) was made on the day the list mentor organizations was published.

My major contributions include:
1. [Massive performance improvement of Kruskal's MST](https://github.com/JuliaGraphs/LightGraphs.jl/pull/843) using the union-find data structure.
2. Implement [Greedy Graph Coloring](https://github.com/JuliaGraphs/LightGraphs.jl/pull/844).
3. [Massive performance improvement of Floyd Warshall APSP](https://github.com/JuliaGraphs/LightGraphs.jl/pull/873)  by making it more cache efficient.

The community was very responsive to issues and pull requests I raised (Especially [Seth Bromberger](https://www.bromberger.com), the co-owner of LightGraphs), which gave me more confidence in my choice.

# Writing a Proposal

After spending 1 month contributing to `LightGraphs`, familiarising myself with `Julia` and the `LightGraphs` code base, I started writing my proposal.

[My Proposal](https://github.com/SohamTamba/GSoC/blob/gh-pages/Proposal.pdf) consists of two portions:
  * **Implementing approximation algorithms and greedy hueristics for graph problems**

There are several NP-Hard problems that occur in practice often. Fast algorithms producing non-optimal solutions for these sort of problems were lacking in LightGraphs.

  * **Creating parallel implementations for algorithms that are inherently slow**

The issue with parallel computing is the overheads caused due to communication between processes could lead to an overall reduction in performance. Algorithms that inherently require more work (relative to the input size) will usually have more scope for improvement through parallelization. Since the algorithms are usually slow, users would be more eager to have a parallel implementation of it. Eg. Floyd Warshall's shortest path is inherently slow because it requires a cubic number of operations with respect to the input.

  * **Creating parallel implementations for algorithms that are important**

Algorithms such as Dijkstra's Shortest Path, Kruskal's minimum spanning tree are inherently fast. But they have several important applications and hence, parallel implementation would be worthwhile if it produced even a modest speed-up. 

# Finding a Committed Mentor

Although I listed `Find a committed mentor` last in my sequence of activities, I would suggest doing it sooner; I later found out that your chances of being acceped fall drastically if a member of the organization has not agreed to work with you before the application period ends. In hindsight, this makes sense: What's the point of having a stellar application if is interested in your project. I almost suffered this fate: I announced my interest in the project in Julia's `Slack` channel only 2 weeks before the application period ended (First month on PR's) and found out that almost everyone was too busy that summer to mentor a student. Luckily, [Divanyansh Srivastava](https://github.com/somil55) came to the rescue in the last few days.

# Lessons Learned
  * **Spend more time on the proposal and less time on pull requests**

Out of the 1.5 months long application period, I spent 1 month making pull requests and only 2 weeks writing the proposal. Trust me, 2 weeks is not enough time to produce a proposal that concisely and clearly explains every detail of your project project. Of course, communicating with the organization before the beginning of the application period would also be helpful.

  * **Communicate with prospective mentors and the community as soon as possible**

As explained earlier, I expressed my interest in working on the project only 2 weeks before the deadline. Discussing with the community earlier would have helped me write a proposal that would interest them more, as well as increase my chances of finding a committed mentor.
