# 🕸️ GRAPH ALGORITHMS 


---

## HOW TO READ THIS SHEET
- Each **subsection** = one **distinct technique**. When you finish a subsection, you know exactly which variation you've mastered.
- Problems that use **multiple techniques** appear in their **primary** technique section, with the secondary technique noted in the "Alternative" column.
- Subsections with 2–3 problems are intentional — those are rare but important variations.

---

## 1. GRAPH TRAVERSAL — DFS / BFS

### 1.1 Basic Grid DFS/BFS — Flood & Count
> **Core idea:** Visit all connected cells of same type. Mark visited. Count components/area.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Flood Fill | Easy | [LC 733](https://leetcode.com/problems/flood-fill/) | DFS/BFS on grid, recolor | - |
| 2 | Number of Islands | Medium | [LC 200](https://leetcode.com/problems/number-of-islands/) | Count DFS components | DSU |
| 3 | Max Area of Island | Medium | [LC 695](https://leetcode.com/problems/max-area-of-island/) | DFS return component size | DSU with size |
| 4 | Maximum Number of Fish in a Grid | Medium | [LC 2658](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/) | DFS sum values in component | DSU |
| 5 | Island Perimeter | Easy | [LC 463](https://leetcode.com/problems/island-perimeter/) | Count border edges per cell | Simple iteration |

### 1.2 Grid DFS/BFS — Border-Based Elimination
> **Core idea:** Start DFS/BFS **from the border**. Any cell reachable from border is "safe"; the rest are enclosed.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Number of Enclaves | Medium | [LC 1020](https://leetcode.com/problems/number-of-enclaves/) | DFS from border, count unreachable | - |
| 7 | Number of Closed Islands | Medium | [LC 1254](https://leetcode.com/problems/number-of-closed-islands/) | DFS, exclude border-connected | - |
| 8 | Surrounded Regions | Medium | [LC 130](https://leetcode.com/problems/surrounded-regions/) | DFS from border, flip remaining | DSU |

### 1.3 Grid DFS/BFS — Two-Grid / Cross-Grid Comparison
> **Core idea:** Use two different grids simultaneously; an island in grid2 is valid only if it's also an island in grid1.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Count Sub Islands | Medium | [LC 1905](https://leetcode.com/problems/count-sub-islands/) | DFS on grid2, validate against grid1 | - |

### 1.4 Grid DFS/BFS — Multi-Source (Simultaneous BFS)
> **Core idea:** Push **all sources** into the queue at step 0. BFS expands all simultaneously — gives minimum distance from nearest source.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 10 | Rotting Oranges | Medium | [LC 994](https://leetcode.com/problems/rotting-oranges/) | All rotten oranges = initial sources | - |
| 11 | 01 Matrix | Medium | [LC 542](https://leetcode.com/problems/01-matrix/) | All 0s = sources, find dist to nearest 0 | DP |
| 12 | As Far from Land as Possible | Medium | [LC 1162](https://leetcode.com/problems/as-far-from-land-as-possible/) | All land = sources, max dist to water | DP |
| 13 | Walls and Gates | Medium (Premium) | [LC 286](https://leetcode.com/problems/walls-and-gates/) | All gates = sources | DP |
| 14 | Map of Highest Peak | Medium | [LC 1765](https://leetcode.com/problems/map-of-highest-peak/) | All water = sources, assign heights | DP |

### 1.5 Grid DFS/BFS — DFS then BFS (Two-Phase)
> **Core idea:** Phase 1: DFS to **identify** a region. Phase 2: BFS to **measure distance** from that region.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Shortest Bridge | Medium | [LC 934](https://leetcode.com/problems/shortest-bridge/) | DFS find island1 → BFS expand to island2 | - |

### 1.6 Grid BFS — Shortest Path in Unweighted Grid
> **Core idea:** BFS always gives shortest path in **unweighted** grids. Each cell = 1 step.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 16 | Shortest Path in Binary Matrix | Medium | [LC 1091](https://leetcode.com/problems/shortest-path-in-binary-matrix/) | 8-directional BFS | A* |
| 17 | Find the Safest Path in a Grid | Medium | [LC 2812](https://leetcode.com/problems/find-the-safest-path-in-a-grid/) | Binary search on answer + multi-source BFS | Dijkstra |
| 18 | Minimum Jumps to Reach Home | Medium | [LC 1654](https://leetcode.com/problems/minimum-jumps-to-reach-home/) | BFS with forbidden positions | - |

### 1.7 Grid — DFS with Direction Simulation
> **Core idea:** Each cell encodes which directions it connects to. DFS follows only valid connection directions.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 19 | Check if There is a Valid Path in a Grid | Medium | [LC 1391](https://leetcode.com/problems/check-if-there-is-a-valid-path-in-a-grid/) | DFS follow pipe directions | DSU |
| 20 | Check if Move is Legal | Medium | [LC 1958](https://leetcode.com/problems/check-if-move-is-legal/) | Simulate 8 directions with rules | - |

### 1.8 Grid — Rectangle / Shape Detection via DFS
> **Core idea:** DFS to find extremes (corners) of a shape rather than just counting cells.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 21 | Find All Groups of Farmland | Medium | [LC 1992](https://leetcode.com/problems/find-all-groups-of-farmland/) | DFS, track top-left & bottom-right | - |

### 1.9 Grid — DFS Backtracking
> **Core idea:** At each cell, try all directions. **Undo** the move (unmark visited) after recursion returns. Used when you need to find specific paths, not just reachable cells.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 22 | Word Search | Medium | [LC 79](https://leetcode.com/problems/word-search/) | DFS backtrack, match characters | Trie (for Word Search II) |

### 1.10 Grid — DFS + Memoization (DP on Grid)
> **Core idea:** DFS on grid where result at each cell depends on neighbors. Cache results — each cell computed once. DAG property required (no revisiting in recursion path).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 23 | Longest Increasing Path in a Matrix | Hard | [LC 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | DFS + memo, increasing = DAG | Topo sort |
| 24 | Out of Boundary Paths | Medium | [LC 576](https://leetcode.com/problems/out-of-boundary-paths/) | DFS + memo, count paths going out | DP |

### 1.11 Grid — DFS + Component Labeling & Merging
> **Core idea:** Assign unique IDs to components (DFS pass 1). Then simulate a change (e.g., flip a cell) and merge adjacent components using their IDs.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Making A Large Island | Hard | [LC 827](https://leetcode.com/problems/making-a-large-island/) | Label components → try flipping each 0 | DSU |

### 1.12 Grid — Cycle Detection in 2D
> **Core idea:** DFS but track the **parent cell** to avoid going back. If you visit an already-visited cell that isn't the parent, you found a cycle.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 26 | Detect Cycles in 2D Grid | Medium | [LC 1559](https://leetcode.com/problems/detect-cycles-in-2d-grid/) | DFS with parent tracking | - |

### 1.13 Standard Graph — DFS/BFS Reachability & Cloning
> **Core idea:** Classic DFS/BFS on adjacency list. Check if nodes are reachable, or deep-copy the graph.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 27 | Clone Graph | Medium | [LC 133](https://leetcode.com/problems/clone-graph/) | DFS/BFS + hashmap to clone nodes | - |
| 28 | Keys and Rooms | Medium | [LC 841](https://leetcode.com/problems/keys-and-rooms/) | DFS reachability, collect keys | - |
| 29 | All Paths From Source to Target | Medium | [LC 797](https://leetcode.com/problems/all-paths-from-source-to-target/) | DFS backtracking on DAG | - |
| 30 | Jump Game III | Medium | [LC 1306](https://leetcode.com/problems/jump-game-iii/) | DFS/BFS, index = node | - |

### 1.14 Standard Graph — Component Counting & Sizing
> **Core idea:** Run DFS/BFS for each unvisited node, increment component count. Track sizes for pair-counting formulas.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 31 | Number of Provinces | Medium | [LC 547](https://leetcode.com/problems/number-of-provinces/) | Count DFS calls on adjacency matrix | DSU |
| 32 | Count Unreachable Pairs of Nodes | Medium | [LC 2316](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/) | Component sizes → pairs = sz*(total-sz) | DSU |
| 33 | Count the Number of Complete Components | Medium | [LC 2685](https://leetcode.com/problems/count-the-number-of-complete-components/) | DFS, check nodes*(nodes-1)/2 = edges | DSU |

### 1.15 Standard Graph — Tree Traversal & Propagation
> **Core idea:** Graph is a tree (no cycles). DFS propagates values (time, cost, count) down or up the tree.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 34 | Time Needed to Inform All Employees | Medium | [LC 1376](https://leetcode.com/problems/time-needed-to-inform-all-employees/) | DFS, time = max child time + self | BFS |
| 35 | Reorder Routes to Lead to City Zero | Medium | [LC 1466](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/) | DFS from 0, count wrong-direction edges | BFS |
| 36 | Minimum Fuel Cost to Report to the Capital | Medium | [LC 2477](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/) | DFS, ceil(subtree_size/seats) per edge | - |

### 1.16 Standard Graph — Degree-Based Logic (No Traversal Needed)
> **Core idea:** Answer is derivable purely from **in-degree / out-degree** counts. No DFS/BFS required.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 37 | Find the Town Judge | Easy | [LC 997](https://leetcode.com/problems/find-the-town-judge/) | in-degree=n-1, out-degree=0 | - |
| 38 | Find Center of Star Graph | Easy | [LC 1791](https://leetcode.com/problems/find-center-of-star-graph/) | Center appears in all edges | - |
| 39 | Minimum Number of Vertices to Reach All Nodes | Medium | [LC 1557](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/) | Nodes with in-degree = 0 | - |
| 40 | Maximal Network Rank | Medium | [LC 1615](https://leetcode.com/problems/maximal-network-rank/) | degree[a]+degree[b]-shared edge | Brute force |

### 1.17 Standard Graph — DFS with Edge Weights (Ratio/Multiplication)
> **Core idea:** Edges have **multiplicative weights**. DFS accumulates product along path to answer queries. This is the gateway to Weighted DSU.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 41 | Evaluate Division | Medium | [LC 399](https://leetcode.com/problems/evaluate-division/) | DFS multiply weights along path | Weighted DSU, Floyd-Warshall |

### 1.18 Graph BFS — Reachability on Non-Grid Structures
> **Core idea:** BFS on adjacency list but nodes are strings, indices, or abstract states (not grid cells).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 42 | Detonate the Maximum Bombs | Medium | [LC 2101](https://leetcode.com/problems/detonate-the-maximum-bombs/) | Build directed graph (circle overlap) → DFS count reachable | - |
| 43 | Similar String Groups | Hard | [LC 839](https://leetcode.com/problems/similar-string-groups/) | Build graph (similar = edge) → count components | DSU |
| 44 | Pacific Atlantic Water Flow | Medium | [LC 417](https://leetcode.com/problems/pacific-atlantic-water-flow/) | BFS from both oceans inward | - |

---

## 2. SHORTEST PATH ALGORITHMS

### 2.1 Dijkstra — Basic (Single Source, Positive Weights)
> **Core idea:** Use a min-heap. Greedily process the nearest unvisited node. Relax its neighbors.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Network Delay Time | Medium | [LC 743](https://leetcode.com/problems/network-delay-time/) | Classic Dijkstra, max of all dist[] | Bellman-Ford, Floyd-Warshall |
| 2 | Minimum Time to Visit Disappearing Nodes | Medium | [LC 3112](https://leetcode.com/problems/minimum-time-to-visit-disappearing-nodes/) | Dijkstra, skip node if dist > disappear time | - |
| 3 | Shortest Distance After Road Addition Queries I | Medium | [LC 3243](https://leetcode.com/problems/shortest-distance-after-road-addition-queries-i/) | Re-run Dijkstra after each edge addition | - |

### 2.2 Dijkstra — Modified Objective (Not Min Sum)
> **Core idea:** Replace "minimize sum" with another objective: minimize max edge, maximize min probability, minimize bottleneck. Same heap structure, different relaxation condition.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | Path with Maximum Probability | Medium | [LC 1514](https://leetcode.com/problems/path-with-maximum-probability/) | Max-heap, relax if prob[u]*edge > prob[v] | Bellman-Ford |
| 5 | Path With Minimum Effort | Medium | [LC 1631](https://leetcode.com/problems/path-with-minimum-effort/) | Minimize max absolute diff along path | Binary search + DSU |
| 6 | Swim in Rising Water | Hard | [LC 778](https://leetcode.com/problems/swim-in-rising-water/) | Minimize max cell value along path | Binary search + DSU |
| 7 | Minimum Path Cost in a Grid | Medium | [LC 2304](https://leetcode.com/problems/minimum-path-cost-in-a-grid/) | Dijkstra/DP row by row | - |
| 8 | The Maze II | Medium (Premium) | [LC 505](https://leetcode.com/problems/the-maze-ii/) | Ball rolls until wall, Dijkstra on stops | - |

### 2.3 Dijkstra — With Extra State (Constrained Shortest Path)
> **Core idea:** State = (node, extra_info). Extra info could be: stops remaining, keys collected, time elapsed. Heap entry = (dist, node, extra_state).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Minimum Cost to Reach Destination in Time | Hard | [LC 1928](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/) | State = (node, time), 2D dist table | DP |
| 10 | Shortest Path in Grid with Obstacles Elimination | Hard | [LC 1293](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/) | State = (r,c,k remaining), BFS/Dijkstra | A* |

### 2.4 Dijkstra — Counting Paths (Dijkstra + DP)
> **Core idea:** While running Dijkstra, also track **how many shortest paths** reach each node. Two arrays: dist[] and count[].

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Number of Ways to Arrive at Destination | Medium | [LC 1976](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/) | dist[] + ways[] updated together | - |
| 12 | Number of Restricted Paths From First to Last Node | Medium | [LC 1786](https://leetcode.com/problems/number-of-restricted-paths-from-first-to-last-node/) | Dijkstra from end → DFS/DP count restricted paths | - |

### 2.5 Dijkstra — Multi-Source / Multi-Run
> **Core idea:** Run Dijkstra from **multiple starting points** or run it **3 times** from different nodes and combine results.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 13 | Minimum Weighted Subgraph With Required Paths | Hard | [LC 2203](https://leetcode.com/problems/minimum-weighted-subgraph-with-the-required-paths/) | Dijkstra from src1, src2, dst → find meeting node | - |
| 14 | Reachable Nodes In Subdivided Graph | Hard | [LC 882](https://leetcode.com/problems/reachable-nodes-in-subdivided-graph/) | Dijkstra, count sub-nodes reachable per edge | - |

### 2.6 Dijkstra — Design / Implementation Problem
> **Core idea:** Wrap Dijkstra inside a class. Re-run on query.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Design Graph With Shortest Path Calculator | Hard | [LC 2642](https://leetcode.com/problems/design-graph-with-shortest-path-calculator/) | Dijkstra per query | - |

### 2.7 Dijkstra — Construction / Reverse Engineering
> **Core idea:** Modify edge weights to **force** a specific shortest path. Run Dijkstra multiple times to verify and construct.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 16 | Modify Graph Edge Weights | Hard | [LC 2699](https://leetcode.com/problems/modify-graph-edge-weights/) | 2-pass Dijkstra to assign -1 edges | - |

### 2.8 Bellman-Ford — K-Step Constrained Paths
> **Core idea:** Relax edges exactly K times. Each relaxation pass = one more step allowed. Use previous-pass distances to avoid using more than K edges.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 17 | Cheapest Flights Within K Stops | Medium | [LC 787](https://leetcode.com/problems/cheapest-flights-within-k-stops/) | Bellman-Ford K+1 iterations, copy prev dist | Modified Dijkstra |

### 2.9 0-1 BFS (Deque BFS)
> **Core idea:** Edge weights are only **0 or 1**. Use deque: weight-0 edges → push front, weight-1 edges → push back. O(V+E), faster than Dijkstra here.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Minimum Cost to Make at Least One Valid Path in a Grid | Hard | [LC 1368](https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/) | Follow arrow=cost 0, change=cost 1 | Dijkstra |
| 19 | Minimum Obstacle Removal to Reach Corner | Hard | [LC 2290](https://leetcode.com/problems/minimum-obstacle-removal-to-reach-corner/) | Empty=cost 0, obstacle=cost 1 | Dijkstra |

### 2.10 BFS — Second Minimum / Modified Distance
> **Core idea:** Track **two** distances per node (min and second-min). Used when you need the second shortest path.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 20 | Second Minimum Time to Reach Destination | Hard | [LC 2045](https://leetcode.com/problems/second-minimum-time-to-reach-destination/) | BFS tracking dist1[] and dist2[] | Dijkstra |

### 2.11 BFS — Shortest Path with Color/Alternating State
> **Core idea:** State includes the **color of the last edge used**. BFS on (node, last_color).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 21 | Shortest Path with Alternating Colors | Medium | [LC 1129](https://leetcode.com/problems/shortest-path-with-alternating-colors/) | BFS state = (node, last_edge_color) | - |

### 2.12 Floyd-Warshall — All-Pairs Shortest Path
> **Core idea:** O(n³) DP. dist[i][j] = min over all intermediate nodes k. Use when n is small (~200) and you need distances between **all pairs**.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 22 | Find the City With Smallest Number of Neighbors | Medium | [LC 1334](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/) | Floyd-Warshall → count reachable per city | Dijkstra from each node |
| 23 | Course Schedule IV | Medium | [LC 1462](https://leetcode.com/problems/course-schedule-iv/) | Floyd-Warshall for reachability | Topo sort |
| 24 | Evaluate Division (All-Pairs) | Medium | [LC 399](https://leetcode.com/problems/evaluate-division/) | Floyd-Warshall with multiplication | DFS, Weighted DSU |

### 2.13 BFS with Bitmask State
> **Core idea:** State = (node, bitmask of collected items). Visited = set of (node, mask) pairs. Guarantees shortest path while collecting all items.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Shortest Path to Get All Keys | Hard | [LC 864](https://leetcode.com/problems/shortest-path-to-get-all-keys/) | State = (r,c, key_bitmask) | Dijkstra |
| 26 | Shortest Path Visiting All Nodes | Hard | [LC 847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) | State = (node, visited_bitmask), multi-source BFS | Dijkstra |

### 2.14 BFS — Abstract State Space (Word/String Transformation)
> **Core idea:** Each state is a string. BFS finds min transformations. Enumerate all 1-char neighbors at each step.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 27 | Word Ladder | Hard | [LC 127](https://leetcode.com/problems/word-ladder/) | BFS on word graph, 1 char diff = edge | Bidirectional BFS |
| 28 | Word Ladder II (All Paths) | Hard | [LC 126](https://leetcode.com/problems/word-ladder-ii/) | BFS to build level graph → backtrack paths | - |
| 29 | Minimum Genetic Mutation | Medium | [LC 433](https://leetcode.com/problems/minimum-genetic-mutation/) | BFS, valid mutations only | - |

### 2.15 BFS — Abstract State Space (Lock / Combination)
> **Core idea:** BFS where state is a configuration (lock combination). Enumerate all next states from current configuration.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 30 | Open the Lock | Medium | [LC 752](https://leetcode.com/problems/open-the-lock/) | BFS on 4-digit state, 8 neighbors | Bidirectional BFS |

---

## 3. TOPOLOGICAL SORT

### 3.1 Topo Sort — Cycle Detection Only
> **Core idea:** Run Kahn's or DFS-coloring. If all nodes are processed → no cycle. If queue empties early → cycle exists.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Course Schedule | Medium | [LC 207](https://leetcode.com/problems/course-schedule/) | Kahn's: if processed < n → cycle | DFS 3-color |
| 2 | Find Eventual Safe States | Medium | [LC 802](https://leetcode.com/problems/find-eventual-safe-states/) | Reverse graph topo → safe = processed | DFS |

### 3.2 Topo Sort — Ordering / Reconstruction
> **Core idea:** Actually output the topological order. Use Kahn's (BFS) or DFS postorder.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 3 | Course Schedule II | Medium | [LC 210](https://leetcode.com/problems/course-schedule-ii/) | Kahn's, collect order | DFS postorder |
| 4 | Alien Dictionary | Hard (Premium) | [LC 269](https://leetcode.com/problems/alien-dictionary/) | Build char order graph → topo | - |
| 5 | Sequence Reconstruction | Medium (Premium) | [LC 444](https://leetcode.com/problems/sequence-reconstruction/) | Unique topo order check | - |
| 6 | Build a Matrix With Conditions | Medium | [LC 2392](https://leetcode.com/problems/build-a-matrix-with-conditions/) | Two independent topo sorts → place in matrix | - |

### 3.3 Topo Sort — Levels (BFS Layer by Layer)
> **Core idea:** Process nodes level by level (all in-degree-0 together = one semester/round). Track depth/level of each node.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 7 | Parallel Courses | Medium (Premium) | [LC 1136](https://leetcode.com/problems/parallel-courses/) | Count BFS levels | - |
| 8 | Parallel Courses III | Hard | [LC 2050](https://leetcode.com/problems/parallel-courses-iii/) | Topo + DP: time[v] = max(time[u]) + duration[v] | - |
| 9 | Minimum Height Trees | Medium | [LC 310](https://leetcode.com/problems/minimum-height-trees/) | Trim leaves level by level until ≤2 nodes remain | - |

### 3.4 Topo Sort + DP (Value Propagation on DAG)
> **Core idea:** After topo sort, run DP: dp[node] = f(dp[predecessors]). The topo order guarantees predecessors are computed first.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 10 | All Ancestors of a Node in DAG | Medium | [LC 2192](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/) | Topo order → propagate ancestor sets forward | DFS |
| 11 | Loud and Rich | Medium | [LC 851](https://leetcode.com/problems/loud-and-rich/) | DFS on DAG → propagate min-quiet person | Topo sort |
| 12 | Longest Path With Different Adjacent Characters | Hard | [LC 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Tree topo → DP longest path with constraint | DFS |
| 13 | Find All Possible Recipes from Given Supplies | Medium | [LC 2115](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/) | Topo sort, ingredients as sources | - |

### 3.5 Topo Sort — Nested (Groups + Items, Two-Level)
> **Core idea:** Two separate topo sorts: one on **groups**, one on **items within groups**. Merge results respecting both orderings.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 14 | Sort Items by Groups Respecting Dependencies | Hard | [LC 1203](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/) | Topo on groups, topo on items inside groups | - |

### 3.6 Topo Sort — Bitmask DP (Parallel Courses II)
> **Core idea:** State = bitmask of completed courses. For each state, try to pick next batch of courses (all prerequisites satisfied).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Parallel Courses II | Hard (Premium) | [LC 1494](https://leetcode.com/problems/parallel-courses-ii/) | Bitmask DP over subsets of completed courses | - |

### 3.7 Topo Sort — Reachability Check (Transitive Closure)
> **Core idea:** For each query (u, v), check if v is reachable from u. Build reachability using topo order + bitsets or BFS.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 16 | Course Schedule IV | Medium | [LC 1462](https://leetcode.com/problems/course-schedule-iv/) | Topo order → propagate reachability sets | Floyd-Warshall |

### 3.8 Topo Sort — Color Ordering (Strange Printer II)
> **Core idea:** Model color containment as a DAG. If color A's rectangle contains color B, A must be printed before B. Topo sort the color DAG.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 17 | Strange Printer II | Hard | [LC 1591](https://leetcode.com/problems/strange-printer-ii/) | Build color containment DAG → topo sort for validity | - |

### 3.9 Functional Graph — Cycle + Tail Structure
> **Core idea:** Every node has **exactly one outgoing edge**. Graph = set of rho (ρ) shapes: tails leading into cycles. Detect cycles via topo (remove non-cycle nodes), then process tails.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Longest Cycle in a Graph | Hard | [LC 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | DFS with timestamps, find back edge cycle length | - |
| 19 | Count Visited Nodes in a Directed Graph | Hard | [LC 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Cycle nodes = cycle_len, tail nodes = dist to cycle + cycle_len | - |
| 20 | Maximum Employees to Be Invited to a Meeting | Hard | [LC 2127](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/) | Functional graph: find cycles, chain length-2 cycles | DFS |

---

## 4. UNION-FIND / DSU

### 4.1 DSU — Basic Connectivity (Find + Union)
> **Core idea:** Two operations: `find(x)` returns root, `union(x,y)` merges components. With path compression + union by rank = near O(1) per operation.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Find if Path Exists in Graph | Easy | [LC 1971](https://leetcode.com/problems/find-if-path-exists-in-graph/) | Union all edges, check find(src)==find(dst) | DFS/BFS |
| 2 | Number of Provinces | Easy | [LC 547](https://leetcode.com/problems/number-of-provinces/) | Count distinct roots after all unions | DFS/BFS |
| 3 | Operations to Make Network Connected | Medium | [LC 1319](https://leetcode.com/problems/number-of-operations-to-make-network-connected/) | Count components - 1 (need ≥ n-1 edges) | DFS |
| 4 | Number of Connected Components | Medium (Premium) | [LC 323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/) | Classic component counting | DFS/BFS |

### 4.2 DSU — Cycle Detection
> **Core idea:** Before `union(u,v)`, check `find(u) == find(v)`. If yes → adding this edge creates a cycle.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Redundant Connection | Medium | [LC 684](https://leetcode.com/problems/redundant-connection/) | First edge where find(u)==find(v) is redundant | DFS |
| 6 | Graph Valid Tree | Medium (Premium) | [LC 261](https://leetcode.com/problems/graph-valid-tree/) | No cycle + exactly n-1 edges + connected | DFS |
| 7 | Redundant Connection II | Hard | [LC 685](https://leetcode.com/problems/redundant-connection-ii/) | Directed tree: handle in-degree-2 node + cycle cases | Complex logic |

### 4.3 DSU — Component Size Tracking
> **Core idea:** Maintain `size[]` array. When merging, update size of new root. Enables O(1) component size queries.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Count Unreachable Pairs of Nodes | Medium | [LC 2316](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/) | size[root] → pairs = sz*(n-sz) | DFS |
| 9 | Most Stones Removed | Medium | [LC 947](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/) | Answer = stones - components (rows+cols treated as nodes) | DFS |
| 10 | Minimize Malware Spread | Medium | [LC 924](https://leetcode.com/problems/minimize-malware-spread/) | For each infected node alone in component, record size | DFS |

### 4.4 DSU — String / Array Grouping
> **Core idea:** DSU groups elements that can be swapped. Within each group, sort independently for the optimal result.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Smallest String With Swaps | Easy | [LC 1202](https://leetcode.com/problems/smallest-string-with-swaps/) | Group swappable indices → sort each group | - |
| 12 | Minimize Hamming Distance After Swap Operations | Medium | [LC 1722](https://leetcode.com/problems/minimize-hamming-distance-after-swap-operations/) | DSU groups → multiset matching within groups | - |
| 13 | Accounts Merge | Medium | [LC 721](https://leetcode.com/problems/accounts-merge/) | Union emails → group by root → sort & merge | DFS |

### 4.5 DSU — Bipartite Check (2-Coloring via DSU)
> **Core idea:** For each edge (u,v), union `u` with `v+n` and `v` with `u+n` (create two virtual copies). If `find(u)==find(u+n)` → not bipartite.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 14 | Is Graph Bipartite? | Medium | [LC 785](https://leetcode.com/problems/is-graph-bipartite/) | DSU with 2n nodes (u and u+n = opposite color) | DFS 2-coloring |
| 15 | Possible Bipartition | Medium | [LC 886](https://leetcode.com/problems/possible-bipartition/) | Same DSU bipartite trick on dislikes graph | DFS |

### 4.6 DSU — Symbolic / Equation Solving
> **Core idea:** Union variables connected by `==`. After all unions, check `!=` constraints: if two variables share a root, they can't be `!=`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 16 | Satisfiability of Equality Equations | Medium | [LC 990](https://leetcode.com/problems/satisfiability-of-equality-equations/) | Union all `==`, then verify `!=` | - |
| 17 | Lexicographically Smallest Equivalent String | Medium | [LC 1061](https://leetcode.com/problems/lexicographically-smallest-equivalent-string/) | Union chars, root = lexicographically smallest | - |

### 4.7 Weighted DSU (DSU with Ratio / Distance on Edges)
> **Core idea:** Each node stores a **weight relative to its parent** (ratio, distance, etc.). `find()` compresses path AND accumulates weight. `union()` sets weight to maintain consistency. This handles multiplicative or additive relationships across edges.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Evaluate Division | Medium | [LC 399](https://leetcode.com/problems/evaluate-division/) | weight[x] = value(x)/value(root). find() multiplies weights along path | DFS, Floyd-Warshall |
| 19 | Number of Good Paths | Hard | [LC 2421](https://leetcode.com/problems/number-of-good-paths/) | Sort edges by max node val → incremental DSU + count same-val nodes per component | - |

### 4.8 DSU — Grid-Based (Cells as Nodes)
> **Core idea:** Flatten 2D grid to 1D DSU index: `id = r*cols + c`. Union adjacent same-value cells. Add a virtual node for "border" connectivity.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 20 | Number of Islands II (Dynamic) | Medium (Premium) | [LC 305](https://leetcode.com/problems/number-of-islands-ii/) | Add land one by one, union with adjacent land | - |
| 21 | Making a Large Island | Hard | [LC 827](https://leetcode.com/problems/making-a-large-island/) | Label islands (DFS), flip each 0 → union neighbor IDs | DFS |
| 22 | Surrounded Regions | Medium | [LC 130](https://leetcode.com/problems/surrounded-regions/) | Virtual border node; border-connected 'O' → union with virtual | DFS/BFS |
| 23 | Regions Cut By Slashes | Medium | [LC 959](https://leetcode.com/problems/regions-cut-by-slashes/) | Each cell = 4 triangles, slash/backslash splits them | DFS |

### 4.9 DSU — Offline Queries (Sort + Incremental DSU)
> **Core idea:** Sort queries and edges together by a key (e.g., edge weight limit). Process queries when the relevant edges have been added.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 24 | Checking Existence of Edge Length Limited Paths | Hard | [LC 1697](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/) | Sort queries and edges by limit → offline DSU | - |

### 4.10 DSU — Dual (Two Independent DSUs)
> **Core idea:** Maintain two separate DSU structures simultaneously (e.g., one for each type of agent). Maximize edges added to both.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Remove Max Edges to Keep Graph Fully Traversable | Hard | [LC 1579](https://leetcode.com/problems/remove-max-number-of-edges-to-keep-graph-fully-traversable/) | 2 DSUs (Alice, Bob); type-3 edges added to both first | - |

### 4.11 DSU — Reverse Deletion (Add in Reverse of Deletion Order)
> **Core idea:** Deletions are hard in DSU. Reverse the problem: process deletions backward as **additions**.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 26 | Bricks Falling When Hit | Hard | [LC 803](https://leetcode.com/problems/bricks-falling-when-hit/) | Process hits in reverse as placements, track roof-connected size | - |

### 4.12 DSU — Time-Based (Reset Between Time Slots)
> **Core idea:** Group events by time. Within same timestamp, union all sharing info. After processing, reset nodes that didn't ultimately get the info.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 27 | Find All People With Secret | Hard | [LC 2092](https://leetcode.com/problems/find-all-people-with-secret/) | Group meetings by time → union → reset non-secret nodes | BFS |

### 4.13 DSU — With Constraints (Restricted Unions)
> **Core idea:** Before performing `union(x,y)`, check all restriction pairs. If merging would put a restricted pair in the same component, reject.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 28 | Process Restricted Friend Requests | Hard | [LC 2076](https://leetcode.com/problems/process-restricted-friend-requests/) | For each request, check restrictions against merged component | - |

### 4.14 DSU — Bitwise AND / OR Aggregation
> **Core idea:** Each component stores an aggregated bitwise value (AND of all edge weights). Used for minimum cost walk queries.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 29 | Minimum Cost Walk in Weighted Graph | Hard | [LC 3108](https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/) | DSU where component value = AND of all edge weights in it | - |

### 4.15 DSU — Incremental with Sorted Nodes
> **Core idea:** Sort nodes by value. Add edges only between nodes of same value or increasing value. Count valid pairs within merged components.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 30 | Number of Good Paths | Hard | [LC 2421](https://leetcode.com/problems/number-of-good-paths/) | Sort by value, add edges incrementally, count same-value pairs | - |

---

## 5. MINIMUM SPANNING TREE (MST)

### 5.1 Kruskal's Algorithm (Sort Edges + DSU)
> **Core idea:** Sort all edges by weight. Greedily add edge if it connects two different components (using DSU). Stops when n-1 edges added.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Min Cost to Connect All Points | Medium | [LC 1584](https://leetcode.com/problems/min-cost-to-connect-all-points/) | Manhattan distance edges → Kruskal | Prim's |
| 2 | Connecting Cities With Minimum Cost | Medium (Premium) | [LC 1135](https://leetcode.com/problems/connecting-cities-with-minimum-cost/) | Classic Kruskal | Prim's |

### 5.2 Prim's Algorithm (Grow Tree from a Node)
> **Core idea:** Start with any node. Greedily add the cheapest edge connecting the current tree to a new node. Use a min-heap of (weight, node).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 3 | Min Cost to Connect All Points | Medium | [LC 1584](https://leetcode.com/problems/min-cost-to-connect-all-points/) | Prim's more efficient for dense graphs | Kruskal |

### 5.3 MST — with Virtual Node
> **Core idea:** Add a virtual node 0 connected to all real nodes with a given cost (e.g., drilling a well). MST on this augmented graph solves the problem.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | Optimize Water Distribution in Village | Hard (Premium) | [LC 1168](https://leetcode.com/problems/optimize-water-distribution-in-a-village/) | Virtual well node → MST | - |

### 5.4 MST — Critical & Pseudo-Critical Edge Classification
> **Core idea:** For each edge: (1) Remove it — if MST weight increases → critical. (2) Force it — if MST weight unchanged → pseudo-critical.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Find Critical and Pseudo-Critical Edges in MST | Hard | [LC 1489](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/) | Kruskal variations: exclude then force each edge | - |

### 5.5 MST — Binary Search on Answer + DSU
> **Core idea:** Binary search on the answer (e.g., max edge weight allowed). For each candidate, check feasibility using DSU connectivity.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Swim in Rising Water | Hard | [LC 778](https://leetcode.com/problems/swim-in-rising-water/) | Binary search on water level → DSU connectivity | Dijkstra |
| 7 | Path With Minimum Effort | Medium | [LC 1631](https://leetcode.com/problems/path-with-minimum-effort/) | Binary search on max diff → BFS/DSU check | Dijkstra |

### 5.6 MST — Offline Queries on Spanning Forest
> **Core idea:** Sort queries by limit. Build MST incrementally (Kruskal). Answer connectivity queries using DSU at appropriate edge-weight thresholds.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Checking Existence of Edge Length Limited Paths | Hard | [LC 1697](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/) | Sort edges + queries by weight → offline DSU | - |

---

## 6. CYCLE DETECTION & BIPARTITE

### 6.1 Cycle Detection — Undirected Graph (DFS with Parent)
> **Core idea:** DFS, tracking parent. If we see an already-visited node that is NOT the parent → back edge → cycle.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Redundant Connection | Medium | [LC 684](https://leetcode.com/problems/redundant-connection/) | Add edges one by one, detect first cycle | DSU |
| 2 | Graph Valid Tree | Medium (Premium) | [LC 261](https://leetcode.com/problems/graph-valid-tree/) | No cycle AND connected | DSU |

### 6.2 Cycle Detection — Directed Graph (DFS 3-Coloring)
> **Core idea:** 3 colors: WHITE (unvisited), GRAY (in current DFS path), BLACK (fully processed). If we hit a GRAY node → back edge → cycle.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 3 | Course Schedule | Medium | [LC 207](https://leetcode.com/problems/course-schedule/) | DFS 3-color on prerequisite graph | Kahn's topo |
| 4 | Find Eventual Safe States | Medium | [LC 802](https://leetcode.com/problems/find-eventual-safe-states/) | Nodes NOT on any cycle = safe | Reverse topo |

### 6.3 Cycle Detection — Directed Graph (Redundant Connection II)
> **Core idea:** Directed tree variant. Two cases: (1) node with in-degree 2, (2) cycle with no in-degree-2 node. Handle both separately.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Redundant Connection II | Hard | [LC 685](https://leetcode.com/problems/redundant-connection-ii/) | Check in-degree-2 node + DSU cycle detection | - |

### 6.4 Cycle Detection — 2D Grid
> **Core idea:** DFS on grid tracking (parent_row, parent_col). If adjacent cell is visited and not the parent cell → cycle.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Detect Cycles in 2D Grid | Medium | [LC 1559](https://leetcode.com/problems/detect-cycles-in-2d-grid/) | DFS with parent cell tracking | DSU |

### 6.5 Cycle Detection — Functional Graph (Every Node Out-Degree = 1)
> **Core idea:** Follow `next[node]` chain. Use visited + in-current-path arrays. Or use Floyd's cycle detection.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 7 | Longest Cycle in a Graph | Hard | [LC 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | DFS with timestamps, cycle length = curr_time - entry_time | - |
| 8 | Count Visited Nodes in a Directed Graph | Hard | [LC 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Find cycle nodes → tails get cycle_len + dist | - |

### 6.6 Bipartite — DFS 2-Coloring
> **Core idea:** Assign color 0 to start node. All neighbors get color 1. All their neighbors get color 0. If any neighbor has same color as current → NOT bipartite.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Is Graph Bipartite? | Medium | [LC 785](https://leetcode.com/problems/is-graph-bipartite/) | BFS/DFS 2-coloring | DSU (2n) |
| 10 | Possible Bipartition | Medium | [LC 886](https://leetcode.com/problems/possible-bipartition/) | Build dislikes graph → 2-color | DSU |

### 6.7 Bipartite — BFS Layering for Group Assignment
> **Core idea:** BFS layer = distance from a source. Even layers = group 1, odd layers = group 2. Maximize groups/BFS depths per component.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Divide Nodes Into the Maximum Number of Groups | Hard | [LC 2493](https://leetcode.com/problems/divide-nodes-into-the-maximum-number-of-groups/) | Must be bipartite, BFS diameter per component | - |

### 6.8 Graph Coloring — More than 2 Colors (Greedy)
> **Core idea:** For each node, assign the smallest color not used by its neighbors. With 4 colors, always valid for planar-like graphs.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Flower Planting With No Adjacent | Medium | [LC 1042](https://leetcode.com/problems/flower-planting-with-no-adjacent/) | Greedy: pick any color not in neighbor colors (max degree ≤ 3) | - |

### 6.9 Graph — Degree-Based Analysis (Trio / Dense Subgraph)
> **Core idea:** Enumerate all triangles/trios. For each, compute a metric based on node degrees. Brute force is O(n³) but with adjacency matrix tricks can be faster.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 13 | Minimum Degree of a Connected Trio | Hard | [LC 1761](https://leetcode.com/problems/minimum-degree-of-a-connected-trio-in-a-graph/) | Enumerate trios, score = deg[a]+deg[b]+deg[c]-6 | - |
| 14 | Maximum Total Importance of Roads | Medium | [LC 2285](https://leetcode.com/problems/maximum-total-importance-of-roads/) | Sort nodes by degree, assign values greedily | - |

---

## 7. ARTICULATION POINTS & BRIDGES

### 7.1 Tarjan's Bridge Finding Algorithm
> **Core idea:** DFS with `disc[]` (discovery time) and `low[]` (lowest disc reachable). Edge (u,v) is a bridge if `low[v] > disc[u]` — means v cannot reach u without this edge.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Critical Connections in a Network | Hard | [LC 1192](https://leetcode.com/problems/critical-connections-in-a-network/) | Classic Tarjan bridge finding | - |

### 7.2 Articulation Points — Application (Min Cuts)
> **Core idea:** Articulation point = node whose removal disconnects the graph. Check if island becomes disconnected after removing 1 or 2 cells.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 2 | Minimum Number of Days to Disconnect Island | Hard | [LC 1568](https://leetcode.com/problems/minimum-number-of-days-to-disconnect-island/) | Answer is 0, 1 (articulation point), or 2 | Brute force |

---

## 8. TREE ALGORITHMS

### 8.1 Tree — Basic DFS (Single Pass, Return Value Up)
> **Core idea:** DFS returns a value from each subtree. Parent combines children's values. Common: return (height, some_metric).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Maximum Depth of Binary Tree | Easy | [LC 104](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | Return max(left, right) + 1 | BFS |
| 2 | Minimum Depth of Binary Tree | Easy | [LC 111](https://leetcode.com/problems/minimum-depth-of-binary-tree/) | Handle leaf vs internal node | BFS |
| 3 | Diameter of Binary Tree | Easy | [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/) | At each node: ans = max(ans, left+right) | - |
| 4 | Count Good Nodes in Binary Tree | Medium | [LC 1448](https://leetcode.com/problems/count-good-nodes-in-binary-tree/) | DFS passing max seen so far | - |
| 5 | Maximum Difference Between Node and Ancestor | Medium | [LC 1026](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/) | DFS passing (min, max) from root to node | - |

### 8.2 Tree — BFS (Level Order / Layer Processing)
> **Core idea:** Process tree level by level. Use queue. Common: capture last element of each level, or process all nodes at depth k.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Binary Tree Right Side View | Medium | [LC 199](https://leetcode.com/problems/binary-tree-right-side-view/) | Last node at each BFS level | DFS with depth |
| 7 | Amount of Time for Binary Tree to Be Infected | Medium | [LC 2385](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/) | Convert to graph → BFS from infected node | DFS |

### 8.3 Tree — Construction from Description
> **Core idea:** Build tree from edge list / parent-child descriptions. Use HashMap to find/create nodes.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Create Binary Tree From Descriptions | Medium | [LC 2196](https://leetcode.com/problems/create-binary-tree-from-descriptions/) | HashMap node creation, find root (no parent) | - |
| 9 | Recover a Tree From Preorder Traversal | Hard | [LC 1028](https://leetcode.com/problems/recover-a-tree-from-preorder-traversal/) | Stack, depth encoded by dashes | Recursion |

### 8.4 Tree — Modification / Deletion
> **Core idea:** DFS returns modified subtree root. Post-order: process children first, then decide current node fate.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 10 | Delete Nodes And Return Forest | Medium | [LC 1110](https://leetcode.com/problems/delete-nodes-and-return-forest/) | Post-order DFS, return null if deleted, add children to result | - |

### 8.5 Tree DP — Rob/Don't-Rob Pattern (Include/Exclude Current Node)
> **Core idea:** At each node, compute two values: result **including** this node, result **excluding** this node. Parent picks the best combination.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | House Robber III | Medium | [LC 337](https://leetcode.com/problems/house-robber-iii/) | Return (rob_this, skip_this) from each node | - |
| 12 | Binary Tree Cameras | Hard | [LC 968](https://leetcode.com/problems/binary-tree-cameras/) | 3 states: covered, uncovered, has camera | - |
| 13 | Minimize the Total Price of Trips | Hard | [LC 2646](https://leetcode.com/problems/minimize-the-total-price-of-the-trips/) | Tree DP (halved, not-halved) after path counting | - |

### 8.6 Tree DP — Path Through Node (Global Answer Updated at Each Node)
> **Core idea:** The longest/max path through a node = left_contribution + right_contribution. Update global answer at each node, but return only the single best arm to parent.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 14 | Binary Tree Maximum Path Sum | Hard | [LC 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | ans = max(ans, left+right+node.val), return max(left,right)+val | - |
| 15 | Longest Univalue Path | Medium | [LC 687](https://leetcode.com/problems/longest-univalue-path/) | Same value extends path, update ans with both arms | - |
| 16 | Longest Path With Different Adjacent Characters | Hard | [LC 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Different char = extend, same char = reset | - |
| 17 | Diameter of Binary Tree | Easy | [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/) | left_height + right_height = path through node | - |

### 8.7 Tree DP — Subtree Aggregation (Sum, Product, Count)
> **Core idea:** Each node computes aggregate over its subtree (sum, count, XOR). Use this to compute the answer at each node.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Distribute Coins in Binary Tree | Medium | [LC 979](https://leetcode.com/problems/distribute-coins-in-binary-tree/) | Flow = |subtree_coins - subtree_nodes|, sum flows | - |
| 19 | Maximum Product of Splitted Binary Tree | Medium | [LC 1339](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/) | subtree_sum * (total - subtree_sum) | - |
| 20 | Count Nodes Equal to Average of Subtree | Medium | [LC 2265](https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/) | Return (sum, count) from subtree | - |
| 21 | Maximum Number of K-Divisible Components | Hard | [LC 2872](https://leetcode.com/problems/maximum-number-of-k-divisible-components/) | Subtree sum % k == 0 → cut edge | - |
| 22 | Minimum Score After Removals on a Tree | Hard | [LC 2538](https://leetcode.com/problems/minimum-score-after-removals-on-a-tree/) | XOR subtree sums, enumerate edge pairs | - |

### 8.8 Tree DP — Re-rooting (Two-Pass)
> **Core idea:** Pass 1 (bottom-up): compute answer assuming current root. Pass 2 (top-down): adjust answer for each new root using parent's values.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 23 | Sum of Distances in Tree | Hard | [LC 834](https://leetcode.com/problems/sum-of-distances-in-tree/) | Pass1: subtree sizes + dist from node 0. Pass2: re-root formula | - |

### 8.9 Tree — LCA (Lowest Common Ancestor) via DFS
> **Core idea:** DFS: if current node is p or q, return it. If both children return non-null → current is LCA. Otherwise return the non-null child.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 24 | Lowest Common Ancestor of a Binary Tree | Medium | [LC 236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | Return p/q if found, LCA when both sides return non-null | Binary lifting |
| 25 | Step-By-Step Directions From a Node to Another | Medium | [LC 2096](https://leetcode.com/problems/step-by-step-directions-from-a-binary-tree-node-to-another/) | LCA + path from LCA to both nodes | - |

### 8.10 Tree — LCA via Binary Lifting (K-th Ancestor)
> **Core idea:** Precompute `ancestor[node][j]` = 2^j-th ancestor. Answer k-th ancestor in O(log n) by decomposing k in binary.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 26 | Kth Ancestor of a Tree Node | Hard | [LC 1483](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) | Binary lifting table, query in O(log n) | - |

### 8.11 Tree — Distance Queries (BFS with Parent Pointers)
> **Core idea:** Convert binary tree to undirected graph (add parent pointers). BFS from target node to find all nodes at distance k.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 27 | All Nodes Distance K in Binary Tree | Medium | [LC 863](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/) | BFS on undirected tree from target | DFS |

### 8.12 Tree — Subtree Matching / Pattern in Tree
> **Core idea:** DFS to check if a linked list path exists going downward through the tree.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 28 | Linked List in Binary Tree | Medium | [LC 1367](https://leetcode.com/problems/linked-list-in-binary-tree/) | DFS: try matching list from each tree node | KMP |

### 8.13 Tree — Strategic Analysis (Size-Based Decision)
> **Core idea:** Compute subtree sizes. Use sizes to determine optimal move (e.g., pick side where opponent cannot win by taking majority).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 29 | Binary Tree Coloring Game | Medium | [LC 1145](https://leetcode.com/problems/binary-tree-coloring-game/) | Win if max(left, right, n-left-right-1) > n/2 | - |

### 8.14 Tree — Depth-Based Node Selection
> **Core idea:** DFS tracking depth. Return the subtree root that contains ALL deepest nodes.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 30 | Smallest Subtree with all the Deepest Nodes | Medium | [LC 865](https://leetcode.com/problems/smallest-subtree-with-all-the-deepest-nodes/) | Return (node, depth); LCA when both sides have same max depth | - |

---

## 9. ADVANCED BFS / STATE SEARCH

### 9.1 BFS — Board/Puzzle State Space
> **Core idea:** Each board configuration is a node. BFS finds minimum moves. Encode state as string or integer for visited set.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Sliding Puzzle | Hard | [LC 773](https://leetcode.com/problems/sliding-puzzle/) | State = board string, neighbors = valid swaps | A* |
| 2 | Minimum Moves to Move a Box to Target | Hard | [LC 1263](https://leetcode.com/problems/minimum-moves-to-move-a-box-to-their-target-location/) | State = (box_pos, player_pos), BFS | A* |
| 3 | Snakes and Ladders | Medium | [LC 909](https://leetcode.com/problems/snakes-and-ladders/) | BFS on 1D positions, handle board mapping | - |

### 9.2 BFS — Jump Graph (Same-Value Teleportation)
> **Core idea:** From each index, add edges to all indices with same value. BFS but delete same-value group after first visit to avoid O(n²) edges.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | Jump Game IV | Hard | [LC 1345](https://leetcode.com/problems/jump-game-iv/) | BFS, group indices by value, clear group after processing | - |

### 9.3 BFS — Route/Bus Graph (BFS on Routes, not Stops)
> **Core idea:** Nodes = bus routes (not stops). BFS finds minimum routes to take. Build stop → routes map.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Bus Routes | Hard | [LC 815](https://leetcode.com/problems/bus-routes/) | BFS on routes, each route = node, stop overlap = edge | - |

### 9.4 BFS — With K-Elimination State
> **Core idea:** State = (position, k_remaining). Each state visited at most once. Eliminates obstacles by spending k budget.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Shortest Path in Grid with Obstacles Elimination | Hard | [LC 1293](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/) | State = (r, c, k), BFS | A* |

### 9.5 BFS — Permutation State Space
> **Core idea:** States are string permutations. BFS finds min swaps to transform one string to another.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 7 | K-Similar Strings | Hard | [LC 854](https://leetcode.com/problems/k-similar-strings/) | BFS on string permutations, only adjacent swaps that fix a char | - |

### 9.6 BFS — Constraint-Based Range BFS (Forbidden Zones)
> **Core idea:** BFS where you can jump forward by [a,b] but certain positions are forbidden. Track visited with both position and direction.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Minimum Jumps to Reach Home | Medium | [LC 1654](https://leetcode.com/problems/minimum-jumps-to-reach-home/) | BFS with (pos, direction) state | - |

### 9.7 BFS — Spreading Process (Fire, Infection, etc.)
> **Core idea:** Precompute fire BFS. Binary search on wait time. For each wait time, check if person's BFS can reach safe house before fire.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Escape the Spreading Fire | Hard | [LC 2258](https://leetcode.com/problems/escape-the-spreading-fire/) | Binary search on wait + compare fire BFS vs person BFS | - |

### 9.8 BFS — With Sorted-Set DSU Optimization (Minimum Reverse Operations)
> **Core idea:** BFS but neighbor enumeration is expensive. Use sorted sets (TreeSet) to find unvisited reachable nodes in O(log n). Mark visited by removing from set.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 10 | Minimum Reverse Operations | Hard | [LC 2612](https://leetcode.com/problems/minimum-reverse-operations/) | BFS + sorted sets as "unvisited node DSU" | - |

### 9.9 DFS — Eulerian Path / Circuit
> **Core idea:** Hierholzer's algorithm: DFS greedily following edges. When stuck, append current node to result. Build circuit backwards.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Reconstruct Itinerary | Hard | [LC 332](https://leetcode.com/problems/reconstruct-itinerary/) | Hierholzer's DFS, sorted neighbors, append on backtrack | - |

### 9.10 BFS — DP Hybrid (Race Car / Position-Velocity State)
> **Core idea:** State = (position, speed). BFS or DP over states. From each state, two moves possible: accelerate or reverse.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Race Car | Hard | [LC 818](https://leetcode.com/problems/race-car/) | BFS/DP on (position, speed) state | - |

### 9.11 Backtracking — Job/Task Assignment with Pruning
> **Core idea:** Assign jobs to workers. Prune: if current assignment already exceeds best answer, backtrack. Sort jobs descending for better pruning.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 13 | Find Minimum Time to Finish All Jobs | Hard | [LC 1723](https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/) | Backtracking + pruning, sorted jobs, binary search on answer | Binary search + DP |

---

## 10. SPECIAL GRAPH PROBLEMS

### 10.1 Weighted DSU — Ratio / Multiplicative Weights
> **Core idea (revisited, full definition):** Each node has a `weight[x]` = ratio of x relative to its parent. On `find(x)`: path compression accumulates the product `weight[x] *= weight[parent[x]]` so weight[x] becomes ratio relative to root. On `union(x, y, ratio)`: set weight to maintain `val(x)/val(y) = ratio`. Query: `val(a)/val(b) = weight[a] / weight[b]` if same component.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Evaluate Division | Medium | [LC 399](https://leetcode.com/problems/evaluate-division/) | weight[x]=x/root, find() multiplies, union() sets cross-ratio | DFS, Floyd-Warshall |

### 10.2 Persistent DSU (Offline Historical Queries)
> **Core idea:** DSU that can answer queries at past states. Use link-cut trees or offline processing with versioned DSU. Supports edge deletions by rebuilding from scratch or using rollback.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 2 | Checking Existence of Edge Length Limited Paths II | Hard | [LC 2846](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths-ii/) | Online queries on MST using persistent/LCT DSU | - |

### 10.3 Functional Graph — Full Analysis (Cycle + Tail)
> *(See also Section 3.9)* Complete reference for problems where every node has exactly one outgoing edge.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 3 | Longest Cycle in a Graph | Hard | [LC 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | Timestamp DFS, back edge = cycle | - |
| 4 | Count Visited Nodes | Hard | [LC 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Cycle nodes + tail distance | - |
| 5 | Maximum Employees to Meeting | Hard | [LC 2127](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/) | Length-2 cycles can chain; larger cycles stand alone | DFS |

### 10.4 DSU with Bitwise Aggregation
> *(See also Section 4.14)* Component-level AND/OR of all edge weights. Query: minimum cost to walk between two nodes in same component.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Minimum Cost Walk in Weighted Graph | Hard | [LC 3108](https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/) | Component AND of edges = min walk cost (AND is monotone decreasing) | - |

### 10.5 DSU + People/Secret Propagation with Time Reset
> *(See also Section 4.12)* Time-sorted events with DSU rollback for failed propagations.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 7 | Find All People With Secret | Hard | [LC 2092](https://leetcode.com/problems/find-all-people-with-secret/) | Time-grouped DSU, reset people not connected to secret-holder | BFS |

### 10.6 Dijkstra — Edge Weight Construction (Reverse Engineering)
> *(See also Section 2.7)* Assign weights to -1 edges such that a target shortest path distance is achieved.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Modify Graph Edge Weights | Hard | [LC 2699](https://leetcode.com/problems/modify-graph-edge-weights/) | 2-pass Dijkstra: pass1 ignores -1 edges, pass2 fills them | - |

---

## 📌 MASTER TECHNIQUE REFERENCE

| Technique | When to Use | Time Complexity | Key Signal in Problem |
|-----------|-------------|-----------------|----------------------|
| **Grid DFS/BFS** | Connected cells, components | O(rows × cols) | "connected", "region", "island" |
| **Border BFS** | Exclude border-connected | O(rows × cols) | "enclosed", "surrounded" |
| **Multi-Source BFS** | Distance from nearest of many sources | O(V+E) | "nearest", "all X expand simultaneously" |
| **Dijkstra** | Weighted shortest path, positive weights | O(E log V) | "minimum cost path", "weighted edges" |
| **Modified Dijkstra** | Non-sum objective | O(E log V) | "minimize max", "maximize min prob" |
| **0-1 BFS** | Edge weights are 0 or 1 only | O(V+E) | "free move" + "cost 1 move" |
| **Bellman-Ford** | K-step constraint, negative weights | O(K × E) | "at most K stops/edges" |
| **Floyd-Warshall** | All pairs, small n | O(n³) | n ≤ 200, "all pairs distances" |
| **BFS + Bitmask** | Collect all items, visiting order matters | O(2^k × V) | "collect all keys/nodes" |
| **Topo Sort (Kahn's)** | Ordering, cycle detection in directed | O(V+E) | "prerequisites", "dependencies" |
| **Functional Graph** | Every node exactly one outgoing edge | O(V) | next[i] defined for all i |
| **Basic DSU** | Dynamic connectivity, component queries | O(α(n)) per op | "connected components", "union-find" |
| **Weighted DSU** | Ratio/distance between elements | O(α(n)) per op | "a/b = ratio", "relative values" |
| **Offline DSU** | Queries with sorted edge/query processing | O(E log E) | "queries with threshold", "offline" |
| **Bipartite Check** | 2-coloring feasibility | O(V+E) | "divide into 2 groups", "no odd cycle" |
| **Tarjan's Bridges** | Critical edges whose removal disconnects | O(V+E) | "critical connections", "bridges" |
| **Tree DP** | Optimize over subtrees | O(n) | "tree", "path through node" |
| **Re-rooting DP** | Answer for each node as root | O(n) | "sum of distances", "all roots" |
| **Binary Lifting (LCA)** | K-th ancestor, LCA in O(log n) | O(n log n) preprocess | "k-th ancestor", "LCA queries" |
| **Eulerian Path** | Visit every **edge** exactly once | O(V+E) | "use every road", "reconstruct itinerary" |
| **BFS State Space** | Puzzle/game with discrete states | O(states) | "minimum moves", "configuration" |

---
> **Legend:** LC = LeetCode | Premium = requires paid subscription | α(n) = inverse Ackermann (practically O(1))
