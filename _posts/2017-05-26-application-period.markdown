---
layout: post
title:  "Application Period"
date:   2017-05-26 14:10:51 +0800
categories: GSoC
tags: GSoC
description: FEB-13-2018 to MAR-27-2018.
---

### Choosing a Project
I was interested in a HPC(High Performanc Computing) project. I started my search in Julia because it is said to be a language that is fast like C and easy to code like python. While skimming the [HPC](https://julialang.org/soc/projects/hpc.html) section of Julia's GSoC projects, I came across the Parallel Graph Development project.

### Contributions to LightGraphs
My first contribution was just [one line](https://github.com/JuliaGraphs/LightGraphs.jl/pull/839) that saved (|E|-|V|+1)*(size of vertex) memory for Prim's algorithm.
My more useful contributions were:
1. Massive improvement in run-time of [Kruskal's MST](https://github.com/JuliaGraphs/LightGraphs.jl/pull/843) using the union-find data structure.
2. Implement [Greedy Coloring](https://github.com/JuliaGraphs/LightGraphs.jl/pull/844).
3. Massive improvement in run-time of [Floyd Warshall](https://github.com/JuliaGraphs/LightGraphs.jl/pull/873) by making it more cache efficient.

### Writing a Proposal
[My Proposal](https://github.com/SohamTamba/GSoC/blob/gh-pages/Proposal.pdf) consists of two portions:
  * Implementing approximation algorithms and greedy hueristics for graph problems.

There are several NP-Hard problems that occur in practice often. Fast algorithms producing non-optimal solutions were lacking in LightGraphs so I proposed to include them.

  * Creating parallel implementations for algorithms that are inherently slow.

The issue with parallel computing is the overheads cause due to communication between processors could lead to an overall reduction in performance. Algorithms that inherently require more work to be done (relative to the input size) will usually have more scope for improvement through parallelization. Eg. Floyd Warshall's shortest path is inherently slow because it requires a cubic number of operations (with respect to the input).

### Lessons Learned
  * Spend more time on the proposal and less time on pull requests. 
I had decided to apply GSoC 1.5 months before the application submission deadline. I spent one month making pull requests and only 2 weeks writing the proposal. Trust me, 2 weeks is not enough time to produce a proposal that concisely and unambigiously explains every detail of your project project. Of course, deciding to apply for GSoC earlier would have also helped my chances.
  * Communicate with prospective mentors and the project owners sooner.
I expressed my interest in working on the project only 2 weeks before the deadline. Interacting with the community earlier would have helped me write proposal that the community would be more interested in.

