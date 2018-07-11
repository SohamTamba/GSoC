---
layout: post
title:  "Application Period"
date:   2018-05-26 14:10:51 +0800
categories: GSoC
tags: GSoC
description: Choosing a project, Making contributions, Writing a proposal
---


Application Period: 13<sup>th</sup> Feb to 27<sup>th</sup> March 2018.

### Choosing a Project
I was interested in a HPC (High Performanc Computing) project. While skimming through the [HPC](https://julialang.org/soc/projects/hpc.html) section of Julia's GSoC projects, I came across the Parallel Graph Development project which meant creating parallel implementation of the graph
functions present in [LightGraphs.jl](https://github.com/JuliaGraphs/LightGraphs.jl). 

I was already familiar with most of the algorithms implemented in the library, which lead me to believe I could make useful contributions to it. I literally chose the second project I explored.

### Contributions to LightGraphs
I spent the first month making contributions to LightGraphs.My [first contribution](https://github.com/JuliaGraphs/LightGraphs.jl/pull/839) is just one line that saved (|E|-|V|+1)*(size of an edge) memory for Prim's MST.
My major contributions include:
1. [Massive performance improvement of Kruskal's MST](https://github.com/JuliaGraphs/LightGraphs.jl/pull/843) using the union-find data structure.
2. Implement [Greedy Graph Coloring](https://github.com/JuliaGraphs/LightGraphs.jl/pull/844).
3. [Massive performance improvement of Floyd Warshall APSP](https://github.com/JuliaGraphs/LightGraphs.jl/pull/873)  by making it more cache efficient.

### Proposal
[My Proposal](https://github.com/SohamTamba/GSoC/blob/gh-pages/Proposal.pdf) consists of two portions:
  * Implementing approximation algorithms and greedy hueristics for graph problems.

There are several NP-Hard problems that occur in practice often. Fast algorithms producing non-optimal solutions for these sort of problems were lacking in LightGraphs.

  * Creating parallel implementations for algorithms that are inherently slow.

The issue with parallel computing is the overheads caused due to communication between processors could lead to an overall reduction in performance. Algorithms that inherently require more work (relative to the input size) will usually have more scope for improvement through parallelization. Since the algorithms are usually slow, users would be more eager to have a parallel implementation of it. Eg. Floyd Warshall's shortest path is inherently slow because it requires a cubic number of operations with respect to the input.

  * Creating parallel implementations for algorithms that are important.

Algorithms such as Dijkstra's Shortest Path, Kruskal's minimum spanning tree are inherently fast.
But they have several important applications. Hence, parallel implementation would be worthwhile
if it produced even a modest speed-up. 

### Lessons Learned
  * Spend more time on the proposal and less time on pull requests. 
I decided to apply for GSoC 1.5 months before the application submission deadline. I spent one month making pull requests and only 2 weeks writing the proposal. Trust me, 2 weeks is not enough time to produce a proposal that concisely and clearly explains every detail of your project project. Of course, deciding to apply for GSoC earlier would help one's chances.
  * Communicate with prospective mentors and the community as soon as you start consider working for 
them. I expressed my interest in working on the project only 2 weeks before the deadline. Interacting with the community earlier would have helped me write a proposal that would interest them more.
