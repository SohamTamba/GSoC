---
layout: post
title:  "Final Report"
date:   2018-08-02 14:10:51 +0530
categories: GSoC
tags: Final-Report
description: Lock-free parallel BFS with dynamic Load-Balancing, Improved sequential PageRank, Implemented parallel random heuristics, Created Project Poster.
---

This post shall be a brief summary on the work I have completed during my GSoC 2018 project titled "Parallel Graph Development". To obtain a more detailed description of my work, please refer to the posts previous to this.

My project consists of three types of activities:

1. Producing parallel implementations of crucial graph algorithms.
2. Improving the performance of the sequential implementation of crucial graph algorithms.
3. Implementing Heuristics to obtain good solutions to crucial NP-Hard graph problems.


The code I have written is available in my [Cloned LightGraphs Repository]("https://github.com/SohamTamba/LightGraphs.jl")

The speed-up is obtained based on benchmarks conducted on a 64-bit linux machine using 4 cores.
For all the algorithms mentioned below except Floyd Warshall APSP, Johnson APSP and Centrality Measures, the input graph is the Ego Twitter Graph with random edge weights. For other the algorithms
the input graph is the FaceBook Combined Graph with random edge weights. The benchmarks are available in previous posts of this blog. For sequential algorithms, the speed-up is measured relative to the pre-existing implementation in LightGraphs. For parallel algorithms, the speed-up is measured relative to either my sequential implementation or the pre-existing sequential implementation in
LightsGraphs (Which ever is faster).


I have attempted to merge my code in LightGraphs.jl which is an optimized graph library written in Julia. I classify the status of my work into three types:

1. Completed and merged into LightGraphs.
2. Completed but yet to be merged into LightGraphs.
3. Completed but not Applicable to LightGraphs.
4. Requires Improvement (Future Work).

In the following sections, I will list the functionality I have implemented, a link to the corresponding branch in my cloned repository and speed-up if applicable. Further details can be found in the posts preceeding this blog.

# 1. Completed and Merged

In this section, I will list the functions that I have implemented and merged into the LightGraphs repository.

- [Kruskal MST](https://github.com/SohamTamba/LightGraphs.jl/tree/kruskal_sort_IDS) **7.70x**
- [Sequential/Parallel Johnson APSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Soham/John_Shortest_Path) **2.10x** 
- [Parallel Floyd Warshall APSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Floyd_Warshall) **1.27x**
- [Parallel Bellman Ford SSSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Bellman_Ford) **1.61x**
- [Parallel PageRank](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Page_Rank) **1.62x**
- [PageRank](https://github.com/SohamTamba/LightGraphs.jl/tree/Seq_PageRank) **3.06x**
- [Load-balanced Graph Partitioning](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Page_Rank)
- [Prim MST](https://github.com/SohamTamba/LightGraphs.jl/tree/Prim_PQ) **7.60x**
- [Dijkstra SSSP I](https://github.com/SohamTamba/LightGraphs.jl/tree/Dijkstra_Performance_Docs) **2.04x**
- [Dijkstra SSSP II](https://github.com/SohamTamba/LightGraphs.jl/tree/Dijkstra_Allocations) **1.17x**

# 2. Completed but not Merged

In this section, I will list the functions that I have implemented but was not able to merge into LightGraphs. Minor changes may be made to the branch after GSoC ends while merging it into LightGraphs.

- [Greedy Heuristics](https://github.com/SohamTamba/LightGraphs.jl/tree/All_Greedy)
1. Minimum Vertex Cover 
2. Minimum Dominating Set
3. Maximum Independent Set
4. Maximum Matching
5. Minimum Vertex Coloring with exchange
6. Vertex Connectivity

- [Parallel Random Heuristics](https://github.com/SohamTamba/LightGraphs.jl/tree/genrate_reduce) **1.88x**
- [Karger Minimum Cut](https://github.com/SohamTamba/LightGraphs.jl/tree/Karger_min_cut)
- [Multi-threaded Centrality Measures](https://github.com/SohamTamba/LightGraphs.jl/tree/Threaded_Centrality)
1. Betweeness Centrality **1.98x**
2. Closeness Centrality **2.18x**
3. Stress Centrality **1.65x**

- [Parallel Breadth-First Search](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_GDistances) **1.79x**


# 3. Completed but not applicable

In this section, I will list the implemented functions that will not be merged into LightGraphs and they are not suitable for LightGraphs.

- [Minimum Steiner Tree](https://github.com/SohamTamba/LightGraphs.jl/tree/GSoC/SteinerTree)
- [Travelling Salesman](https://github.com/SohamTamba/LightGraphs.jl/tree/GSoC/TravellingSalesman)

# 4. Requires Improvement (Future Work)

In this section, I will list the parallel implementation of algorithms that 
will not be merged into LightGraphs. These are parallel implementations of crucial algorithms that are slower than the sequential implementation.

- [Parallel Kruskal MST](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Kruskal)
- [Parallel Prim MST](https://github.com/SohamTamba/LightGraphs.jl/tree/BatchPriorityQueue_Parallel_Dijkstra_Prim)
- [Parallel Dijkstra SSSP](https://github.com/SohamTamba/LightGraphs.jl/tree/BatchPriorityQueue_Parallel_Dijkstra_Prim)

The description of my attempt to produce a parallel implementation can be obtained in the appropriate
 posts of this blog.

Julia's shared memory parallelism functionality was introduced fairly recently. After it matures more, I would probably be possible to obtain good speed-ups through a parallel implementations.

# Acknowledgements

I would like to thank my mentor, **Divyansh Srivastav** and LightGraphs co-owner **Seth Bromberger** for reviewing my code and providing valuable suggestions to improve it.
