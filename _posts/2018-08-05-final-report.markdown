---
layout: post
title:  "Final Report"
date:   2018-08-05 14:10:51 +0530
categories: GSoC
tags: Final-Report
description: Concise summary of tasks completed during GSoC 2018.
---

This post shall be a brief summary on the work I have completed during my GSoC 2018 project titled "Parallel Graph Development". To obtain a more detailed description of my work, please refer to the posts previous to this.

My project consists of three types of activities:

1. Producing parallel implementations of crucial graph algorithms.
2. Improving the performance of the sequential implementation of crucial graph algorithms.
3. Implementing Heuristics to obtain good solutions to crucial NP-Hard graph problems.


The code I have written is available in my [Cloned LightGraphs Repository]("https://github.com/SohamTamba/LightGraphs.jl")

The speed-up is obtained based on benchmarks conducted on a 64-bit linux machine using 4 cores.
For most of the algorithms mentioned below benchmarks were obtained on the following graphs with random edge weights:


<style>

table{
    border-collapse: collapse;
    border-spacing: 0;
    border:2px solid #ff0000;
}

th{
    border:2px solid #000000;
}

td{
    border:1px solid #000000;
}
</style>

---

No. | Graph | Vertices | Edges 
:---: | :---------: | :------------: | :-----------------:
1 | Twitter Social Circles | 81,306 | 1,342,310 
2 | Astro-Physics Collaboration | 17,903 | 197,031
3 | Facebook Social Circles | 4,039 | 88,234 

---



**Speed-up on parallelization with 4 cores:**

Algorithm | Twitter | Astro-Physics | Facebook
---------: | :------------: | :-----------------: | :-------:
Breadth-First Search | 1.80 | 2.08 | 2.12
PageRank | 1.77 | 1.54 | 1.65
Bellman Ford SSSP | - | - | 1.88
Floyd Warshall APSP | - | - | 1.27
Johnson APSP | - | -  |2.10
Randomized Heuristic | 1.88 | 1.70 | 1.66
Betweenness Centrality | - | - | 1.96
Closeness Centrality | - | - | 2.17
Stress Centrality | - | - | 1.66


---

**Speed-up on sequential optimization:**

Algorithm | Twitter | Astro-Physics | Facebook
---------: | :------------: | :-----------------: | :-------:
PageRank | 3.05 | 3.37 | 3.17
Dijkstra SSSP | 2.80 | 2.10 | 1.68
Prim MST | 7.65 | 4.25 | 4.05
Kruskal MST | 7.70 | 3.37 | 2.80

---

I have attempted to merge my code in LightGraphs.jl which is an optimized graph library written in Julia. I classify the status of my work into three types:

1. Completed and merged into LightGraphs.
2. Completed but yet to be merged into LightGraphs.
3. Completed but not Applicable to LightGraphs.
4. Requires Improvement (Future Work).

In the following sections, I will list the functionality I have implemented, a link to the corresponding branch in my cloned repository. Further details can be found in the posts preceeding this blog.

# 1. Completed and Merged

In this section, I will list the functions that I have implemented and merged into the LightGraphs repository.

- [Kruskal MST](https://github.com/SohamTamba/LightGraphs.jl/tree/kruskal_sort_IDS) 
- [Sequential/Parallel Johnson APSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Soham/John_Shortest_Path)  
- [Parallel Floyd Warshall APSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Floyd_Warshall) 
- [Parallel Bellman Ford SSSP](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Bellman_Ford) 
- [Parallel PageRank](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Page_Rank)
- [PageRank](https://github.com/SohamTamba/LightGraphs.jl/tree/Seq_PageRank) 
- [Load-balanced Partitioning](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_Page_Rank)
- [Prim MST](https://github.com/SohamTamba/LightGraphs.jl/tree/Prim_PQ) 
- [Dijkstra SSSP I](https://github.com/SohamTamba/LightGraphs.jl/tree/Dijkstra_Performance_Docs) 
- [Dijkstra SSSP II](https://github.com/SohamTamba/LightGraphs.jl/tree/Dijkstra_Allocations) 

# 2. Completed but not Merged

In this section, I will list the functions that I have implemented but was not able to merge into LightGraphs. Minor changes may be made to the branch after GSoC ends while merging it into LightGraphs.

- [Greedy Heuristics](https://github.com/SohamTamba/LightGraphs.jl/tree/All_Greedy)
1. Minimum Vertex Cover 
2. Minimum Dominating Set
3. Maximum Independent Set
4. Maximum Matching
5. Minimum Vertex Coloring with exchange
6. Vertex Connectivity

- [Parallel Random Heuristics](https://github.com/SohamTamba/LightGraphs.jl/tree/genrate_reduce) 
- [Karger Minimum Cut](https://github.com/SohamTamba/LightGraphs.jl/tree/Karger_min_cut)
- [Multi-threaded Centrality Measures](https://github.com/SohamTamba/LightGraphs.jl/tree/Threaded_Centrality)
1. Betweeness Centrality 
2. Closeness Centrality 
3. Stress Centrality 

- [Parallel Breadth-First Search](https://github.com/SohamTamba/LightGraphs.jl/tree/Parallel_GDistances)


# 3. Completed but not Applicable

In this section, I will list the implemented functions that will not be merged into LightGraphs as they are not suitable for LightGraphs.

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
