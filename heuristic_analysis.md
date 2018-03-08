# Heuristic Analysis

The analysis in this paper is the comparison of non-heuristic and heuristic search result metrics for the 3 problems.



## Problem 1

|                                     | Expansions | Goal Tests | New Nodes |Plan length|Time Elapsed|
| ----------------------------------- | ---------- | ---------- | --------- | --------- | --------- |
| breadth_first_search                | 43 | 56 | 180 |6|0.0301|
| breadth_first_tree_search           | 1458 | 1459 | 5960 |6|0.8519|
| depth_first_graph_search            | 21 | 22 | 84 |20|0.0135|
| depth_limited_search                | 101 | 271 | 414 |50|0.0931|
| uniform_cost_search                 | 55 | 57 | 224 |6|0.0373|
| recursive_best_first_search h_1     | 4229 | 4230 | 17023 |6|2.5315|
| greedy_best_first_graph_search h_1  | 7 | 9 | 28 |6|0.0065|
| astar_search h_1                    | 55 | 57 | 224 |6|0.0423|
| astar_search h_ignore_preconditions | 41 | 43 | 170 |6|0.0399|
| astar_search h_pg_levelsum          | 11 | 13 | 50 |6|0.7124|

Each algorithm can get the final result.
In non-heuristic search algorithms, greedy_best_first_graph_search performs best.
A* search with h_ignore_preconditions works best in heuristic search algorithms.
In both categories, the two algorithms, Expansions, Goal Tests, and New Nodes, are the least expensive and consume less time.

### Optimal plan:

Load(C1, P1, SFO)
Fly(P1, SFO, JFK)
Load(C2, P2, JFK)
Fly(P2, JFK, SFO)
Unload(C1, P1, JFK)
Unload(C2, P2, SFO)

## Problem 2

|                                     | Expansions | Goal Tests | New Nodes |Plan length|Time Elapsed|
| ----------------------------------- | ---------- | ---------- | --------- | --------- | --------- |
| breadth_first_search                | 3343 | 4609 | 30509 |9|8.5986|
| breadth_first_tree_search           | Failed | Failed | Failed |Failed|Failed|
| depth_first_graph_search            | 624 | 625 | 5602 |619|3.4793|
| depth_limited_search                | Failed | Failed | Failed |Failed|Failed|
| uniform_cost_search                 | 4849 | 4851 | 44001 |9|11.8668|
| recursive_best_first_search h_1     | Failed | Failed | Failed |Failed|Failed|
| greedy_best_first_graph_search h_1  | 996 | 968 | 8694 |16|2.4523|
| astar_search h_1                    | 4849 | 4851 | 44001 |9|12.2146|
| astar_search h_ignore_preconditions | 1443 | 1445 | 13234 |9|4.9214|
| astar_search h_pg_levelsum          | 85 | 87 | 831 |9|0.7124|

The complexity of Question 2 increased, so breadth_first_tree_search, depth_limited_search and recursive_best_first_search with h_1 did not get results for a limited time.
In non-heuristic search algorithms, greedy_best_first_graph_search uses less time, so the best performance.
In heuristic search algorithms, from time or other score, it appears  that A* search with h_ignore_preconditions works best.

### Optimal plan:

Load(C1, P1, SFO)
Fly(P1, SFO, JFK)
Load(C2, P2, JFK)
Fly(P2, JFK, SFO)
Load(C3, P3, ATL)
Fly(P3, ATL, SFO)
Unload(C3, P3, SFO)
Unload(C1, P1, JFK)
Unload(C2, P2, SFO)

## Problem 3

|                                     | Expansions | Goal Tests | New Nodes |Plan length|Time Elapsed|
| ----------------------------------- | ---------- | ---------- | --------- | --------- | --------- |
| breadth_first_search                | 14663 | 18098 | 129631 |12|112.2314|
| breadth_first_tree_search           | Failed | Failed | Failed |Failed|Failed|
| depth_first_graph_search            | 408 | 409 | 3364 |392|1.6237|
| depth_limited_search                | Failed | Failed | Failed |Failed|Failed|
| uniform_cost_search                 | 18235 | 18237 | 159716 |12|76.6277|
| recursive_best_first_search h_1     | Failed | Failed | Failed |Failed|Failed|
| greedy_best_first_graph_search h_1  | 5462 | 5464 | 48176 |21|20.4434|
| astar_search h_1                    | 18235 | 18237 | 159716 |12|75.9731|
| astar_search h_ignore_preconditions | 4945 | 4947 | 43991 |12|21.5731|
| astar_search h_pg_levelsum          | 290 | 292 | 2670 |12|430.3872|

As in the case of Problem 2, the same three algorithms do not calculate the result.

In non-heuristic algorithms, uniform_cost_search became the winner. Although depth_first_graph_search takes the shortest amount of time, the plan length does not meet the requirements.
A* search with h_ignore_preconditions works best in heuristics. Although A* with h_pg_levelsum's Expansions, Goal Tests, and New Nodes are lower, calculations are much slower.

### Optimal plan:

Load(C1, P1, SFO)
Fly(P1, SFO, ATL)
Load(C3, P1, ATL)
Fly(P1, ATL, JFK)
Unload(C3, P1, JFK)
Load(C2, P2, JFK)
Fly(P2, JFK, ORD)
Load(C4, P2, ORD)
Fly(P2, ORD, SFO)
Unload(C4, P2, SFO)
Unload(C1, P1, JFK)
Unload(C2, P2, SFO)



## Summary

Neither the positive search nor the reverse search is as good as the heuristic. 

A* search with ignoring preconditions works best for all A* algorithms. Because it relaxed the problem but not overestimating the goal. Its heuristic is simpler than level-sum heuristic .It drops all preconditions from actions, and every actions becomes applicable in every state, and any single goal fluent can be achieved in one step.

Depth-first search results in unlimited execution because there is no predefined maximum search depth.So you can solve this problem by defining a maximum search depth in advance.

