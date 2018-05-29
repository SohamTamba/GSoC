---
layout: post
title:  "Application Period"
date:   2018-05-26 14:10:51 +0800
categories: GSoC
tags: GSoC
description: FEB-13-2018 to MAR-27-2018.
---

### Choosing a Project
I was interested in a HPC (High Performanc Computing) project. I started my search in Julia because it is said to be a language that is fast like C and easy to code like python. While skimming through the [HPC](https://julialang.org/soc/projects/hpc.html) section of Julia's GSoC projects, I came across the Parallel Graph Development project.

### Contributions to LightGraphs
My first contribution is just [one line](https://github.com/JuliaGraphs/LightGraphs.jl/pull/839) that saved (|E|-|V|+1)*(size of vertex) memory for Prim's algorithm.
My major contributions include:
1. [Massive improvement](https://github.com/JuliaGraphs/LightGraphs.jl/pull/843) in run-time of Kruskal's MST using the union-find data structure.
2. Implement [Greedy Coloring](https://github.com/JuliaGraphs/LightGraphs.jl/pull/844).
3. [Massive improvement](https://github.com/JuliaGraphs/LightGraphs.jl/pull/873) in run-time of Floyd Warshall by making it more cache efficient.

More details are available in [my proposal](https://github.com/SohamTamba/GSoC/blob/gh-pages/Proposal.pdf).

### Writing a Proposal
[My Proposal](https://github.com/SohamTamba/GSoC/blob/gh-pages/Proposal.pdf) consists of two portions:
  * Implementing approximation algorithms and greedy hueristics for graph problems.

There are several NP-Hard problems that occur in practice often. Fast algorithms producing non-optimal solutions for these sort of problems were lacking in LightGraphs.

  * Creating parallel implementations for algorithms that are inherently slow.

The issue with parallel computing is the overheads caused due to communication between processors could lead to an overall reduction in performance. Algorithms that inherently require more work (relative to the input size) will usually have more scope for improvement through parallelization. Since the algorithms are usually slow, users would be more eager to have a parallel implementation of it. Eg. Floyd Warshall's shortest path is inherently slow because it requires a cubic number of operations with respect to the input.

### Lessons Learned
  * Spend more time on the proposal and less time on pull requests. 
I decided to apply for GSoC 1.5 months before the application submission deadline. I spent one month making pull requests and only 2 weeks writing the proposal. Trust me, 2 weeks is not enough time to produce a proposal that concisely and clearly explains every detail of your project project. Of course, deciding to apply for GSoC earlier would help one's chances.
  * Communicate with prospective mentors and the project owner as soon as possible.
I expressed my interest in working on the project only 2 weeks before the deadline. Interacting with the community earlier would have helped me write a proposal that the community would be more interested in.
