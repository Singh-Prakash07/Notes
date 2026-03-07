
### 1. GRAPH TRAVERSAL (DFS/BFS) - 
#### 1.1 Basic Grid Traversal (Easy-Medium) -
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Island Perimeter | Easy | [LeetCode 463](https://leetcode.com/problems/island-perimeter/) | Grid counting | Simple iteration |
| 2 | Flood Fill | Easy | [LeetCode 733](https://leetcode.com/problems/flood-fill/) | Basic DFS/BFS | - |
| 3 | Find Center of Star Graph | Easy | [LeetCode 1791](https://leetcode.com/problems/find-center-of-star-graph/) | Degree check | - |
| 4 | Find the Town Judge | Easy | [LeetCode 997](https://leetcode.com/problems/find-the-town-judge/) | In/Out degree | - |
| 5 | Number of Islands | Medium | [LeetCode 200](https://leetcode.com/problems/number-of-islands/) | DFS/BFS on grid | DSU |
| 6 | Max Area of Island | Medium | [LeetCode 695](https://leetcode.com/problems/max-area-of-island/) | DFS/BFS with size | DSU with size |
| 7 | Number of Enclaves | Medium | [LeetCode 1020](https://leetcode.com/problems/number-of-enclaves/) | DFS/BFS from borders | - |
| 8 | Number of Closed Islands | Medium | [LeetCode 1254](https://leetcode.com/problems/number-of-closed-islands/) | DFS/BFS exclude borders | - |
| 9 | Count Sub Islands | Medium | [LeetCode 1905](https://leetcode.com/problems/count-sub-islands/) | Grid comparison DFS | - |
| 10 | Find All Groups of Farmland | Medium | [LeetCode 1992](https://leetcode.com/problems/find-all-groups-of-farmland/) | DFS rectangle detection | - |
| 11 | Maximum Number of Fish in a Grid | Medium | [LeetCode 2658](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/) | DFS/BFS | DSU |
| 12 | Check if Move is Legal | Medium | [LeetCode 1958](https://leetcode.com/problems/check-if-move-is-legal/) | Simulation | - |
| 13 | Surrounded Regions | Medium | [LeetCode 130](https://leetcode.com/problems/surrounded-regions/) | DFS/BFS from borders | DSU |
| 14 | Pacific Atlantic Water Flow | Medium | [LeetCode 417](https://leetcode.com/problems/pacific-atlantic-water-flow/) | DFS/BFS from both oceans | - |
| 15 | Check if There is a Valid Path in a Grid | Medium | [LeetCode 1391](https://leetcode.com/problems/check-if-there-is-a-valid-path-in-a-grid/) | DFS with directions | DSU |
#### 1.2 Grid Backtracking & Advanced Patterns - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 16 | Word Search | Medium | [LeetCode 79](https://leetcode.com/problems/word-search/) | DFS backtracking | Trie (for multiple words) |
| 17 | Out of Boundary Paths | Medium | [LeetCode 576](https://leetcode.com/problems/out-of-boundary-paths/) | DFS + memoization | DP |
| 18 | Longest Increasing Path in a Matrix | Hard | [LeetCode 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | DFS + memo (DP) | - |
| 19 | Making A Large Island | Hard | [LeetCode 827](https://leetcode.com/problems/making-a-large-island/) | DFS + component tracking | DSU |
| 20 | Detect Cycles in 2D Grid | Medium | [LeetCode 1559](https://leetcode.com/problems/detect-cycles-in-2d-grid/) | DFS cycle detection | - |
| 21 | Count the Number of Complete Components | Medium | [LeetCode 2685](https://leetcode.com/problems/count-the-number-of-complete-components/) | DFS component analysis | DSU |
| 22 | Detonate the Maximum Bombs | Medium | [LeetCode 2101](https://leetcode.com/problems/detonate-the-maximum-bombs/) | DFS reachability | - |
| 23 | Jump Game III | Medium | [LeetCode 1306](https://leetcode.com/problems/jump-game-iii/) | DFS/BFS | - |
| 24 | Similar String Groups | Hard | [LeetCode 839](https://leetcode.com/problems/similar-string-groups/) | DFS/BFS grouping | DSU |
| 25 | Maximal Network Rank | Medium | [LeetCode 1615](https://leetcode.com/problems/maximal-network-rank/) | Graph degree | Brute force |
#### 1.3 Multi-Source BFS - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 26 | Rotting Oranges | Medium | [LeetCode 994](https://leetcode.com/problems/rotting-oranges/) | Multi-source BFS | - |
| 27 | 01 Matrix | Medium | [LeetCode 542](https://leetcode.com/problems/01-matrix/) | Multi-source BFS | DP |
| 28 | As Far from Land as Possible | Medium | [LeetCode 1162](https://leetcode.com/problems/as-far-from-land-as-possible/) | Multi-source BFS | DP |
| 29 | Walls and Gates | Medium (Premium) | [LeetCode 286](https://leetcode.com/problems/walls-and-gates/) | Multi-source BFS | DP |
| 30 | Shortest Bridge | Medium | [LeetCode 934](https://leetcode.com/problems/shortest-bridge/) | DFS + BFS | - |
| 31 | Shortest Path in Binary Matrix | Medium | [LeetCode 1091](https://leetcode.com/problems/shortest-path-in-binary-matrix/) | BFS | A* |
| 32 | Find the Safest Path in a Grid | Medium | [LeetCode 2812](https://leetcode.com/problems/find-the-safest-path-in-a-grid/) | Binary search + multi-source BFS | Dijkstra |
| 33 | Minimum Jumps to Reach Home | Medium | [LeetCode 1654](https://leetcode.com/problems/minimum-jumps-to-reach-home/) | BFS with constraints | - |
| 34 | Escape the Spreading Fire | Hard | [LeetCode 2258](https://leetcode.com/problems/escape-the-spreading-fire/) | Binary search + BFS | - |
| 35 | Minimum Reverse Operations | Hard | [LeetCode 2612](https://leetcode.com/problems/minimum-reverse-operations/) | BFS with DSU | - |
#### 1.4 Standard Graph Traversal - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 36 | Clone Graph | Medium | [LeetCode 133](https://leetcode.com/problems/clone-graph/) | DFS/BFS with hashmap | - |
| 37 | Number of Provinces | Medium | [LeetCode 547](https://leetcode.com/problems/number-of-provinces/) | DFS/BFS components | DSU |
| 38 | Keys and Rooms | Medium | [LeetCode 841](https://leetcode.com/problems/keys-and-rooms/) | DFS/BFS reachability | - |
| 39 | All Paths From Source to Target | Medium | [LeetCode 797](https://leetcode.com/problems/all-paths-from-source-to-target/) | DFS backtracking | - |
| 40 | Reorder Routes to Lead to City Zero | Medium | [LeetCode 1466](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/) | DFS/BFS with direction | - |
| 41 | Time Needed to Inform All Employees | Medium | [LeetCode 1376](https://leetcode.com/problems/time-needed-to-inform-all-employees/) | DFS/BFS on tree | - |
| 42 | Minimum Number of Vertices to Reach All Nodes | Medium | [LeetCode 1557](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/) | In-degree check | - |
| 43 | Minimum Fuel Cost to Report to the Capital | Medium | [LeetCode 2477](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/) | Tree DFS | - |
| 44 | Count Unreachable Pairs of Nodes | Medium | [LeetCode 2316](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/) | DFS component sizes | DSU |
| 45 | Evaluate Division | Medium | [LeetCode 399](https://leetcode.com/problems/evaluate-division/) | DFS with weights | Weighted DSU, Floyd-Warshall |

### 2. SHORTEST PATH ALGORITHMS - 30 Problems
#### 2.1 Dijkstra's Algorithm - 15 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Network Delay Time | Medium | [LeetCode 743](https://leetcode.com/problems/network-delay-time/) | Dijkstra basic | Bellman-Ford, Floyd-Warshall |
| 2 | Path with Maximum Probability | Medium | [LeetCode 1514](https://leetcode.com/problems/path-with-maximum-probability/) | Modified Dijkstra | Bellman-Ford |
| 3 | The Maze II | Medium (Premium) | [LeetCode 505](https://leetcode.com/problems/the-maze-ii/) | Dijkstra / BFS | - |
| 4 | Swim in Rising Water | Hard | [LeetCode 778](https://leetcode.com/problems/swim-in-rising-water/) | Dijkstra / Binary Search | DSU |
| 5 | Path With Minimum Effort | Medium | [LeetCode 1631](https://leetcode.com/problems/path-with-minimum-effort/) | Dijkstra / Binary Search | DSU |
| 6 | Minimum Weighted Subgraph With Required Paths | Hard | [LeetCode 2203](https://leetcode.com/problems/minimum-weighted-subgraph-with-the-required-paths/) | 3x Dijkstra | - |
| 7 | Number of Ways to Arrive at Destination | Medium | [LeetCode 1976](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/) | Dijkstra + DP | - |
| 8 | Design Graph With Shortest Path Calculator | Hard | [LeetCode 2642](https://leetcode.com/problems/design-graph-with-shortest-path-calculator/) | Dijkstra implementation | - |
| 9 | Minimum Time to Visit Disappearing Nodes | Medium | [LeetCode 3112](https://leetcode.com/problems/minimum-time-to-visit-disappearing-nodes/) | Dijkstra with time | - |
| 10 | Minimum Cost to Reach Destination in Time | Hard | [LeetCode 1928](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/) | Dijkstra with constraints | DP |
| 11 | Reachable Nodes In Subdivided Graph | Hard | [LeetCode 882](https://leetcode.com/problems/reachable-nodes-in-subdivided-graph/) | Dijkstra | - |
| 12 | Minimum Score of a Path Between Two Cities | Medium | [LeetCode 2492](https://leetcode.com/problems/minimum-score-of-a-path-between-two-cities/) | DFS/BFS or DSU | DSU |
| 13 | Modify Graph Edge Weights | Hard | [LeetCode 2699](https://leetcode.com/problems/modify-graph-edge-weights/) | Dijkstra + construction | - |
| 14 | Shortest Distance After Road Addition Queries I | Medium | [LeetCode 3243](https://leetcode.com/problems/shortest-distance-after-road-addition-queries-i/) | Multiple Dijkstra | - |
| 15 | Number of Restricted Paths From First to Last Node | Medium | [LeetCode 1786](https://leetcode.com/problems/number-of-restricted-paths-from-first-to-last-node/) | Dijkstra + DFS/DP | - |
#### 2.2 Bellman-Ford & Special Cases - 5 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 16 | Cheapest Flights Within K Stops | Medium | [LeetCode 787](https://leetcode.com/problems/cheapest-flights-within-k-stops/) | Bellman-Ford / BFS | Dijkstra modified |
| 17 | Minimum Cost to Make at Least One Valid Path | Hard | [LeetCode 1368](https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/) | 0-1 BFS / Dijkstra | DSU |
| 18 | Minimum Obstacle Removal to Reach Corner | Hard | [LeetCode 2290](https://leetcode.com/problems/minimum-obstacle-removal-to-reach-corner/) | 0-1 BFS | Dijkstra |
| 19 | Second Minimum Time to Reach Destination | Hard | [LeetCode 2045](https://leetcode.com/problems/second-minimum-time-to-reach-destination/) | Modified BFS | Dijkstra |
| 20 | Shortest Path with Alternating Colors | Medium | [LeetCode 1129](https://leetcode.com/problems/shortest-path-with-alternating-colors/) | BFS with color state | - |
#### 2.3 Floyd-Warshall (All Pairs) - 3 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 21 | Find the City With Smallest Number of Neighbors | Medium | [LeetCode 1334](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/) | Floyd-Warshall | Dijkstra from all |
| 22 | Course Schedule IV | Medium | [LeetCode 1462](https://leetcode.com/problems/course-schedule-iv/) | Floyd-Warshall / Topo | DFS reachability |
| 23 | Evaluate Division | Medium | [LeetCode 399](https://leetcode.com/problems/evaluate-division/) | Floyd-Warshall / DFS | Weighted DSU |
#### 2.4 BFS with State/Bitmask - 7 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 24 | Shortest Path to Get All Keys | Hard | [LeetCode 864](https://leetcode.com/problems/shortest-path-to-get-all-keys/) | BFS with bitmask | Dijkstra |
| 25 | Shortest Path Visiting All Nodes | Hard | [LeetCode 847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) | BFS with bitmask | Dijkstra |
| 26 | Shortest Path in Grid with Obstacles Elimination | Hard | [LeetCode 1293](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/) | BFS with state | A* |
| 27 | Word Ladder | Hard | [LeetCode 127](https://leetcode.com/problems/word-ladder/) | BFS | Bidirectional BFS |
| 28 | Word Ladder II | Hard | [LeetCode 126](https://leetcode.com/problems/word-ladder-ii/) | BFS + backtracking | - |
| 29 | Minimum Genetic Mutation | Medium | [LeetCode 433](https://leetcode.com/problems/minimum-genetic-mutation/) | BFS | - |
| 30 | Open the Lock | Medium | [LeetCode 752](https://leetcode.com/problems/open-the-lock/) | BFS | Bidirectional BFS |

### 3. TOPOLOGICAL SORT - 20 Problems
#### 3.1 Basic Topological Sort (Kahn's & DFS) - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Course Schedule | Medium | [LeetCode 207](https://leetcode.com/problems/course-schedule/) | Cycle detection / Topo | DFS with colors |
| 2 | Course Schedule II | Medium | [LeetCode 210](https://leetcode.com/problems/course-schedule-ii/) | Kahn's algorithm | DFS postorder |
| 3 | Find Eventual Safe States | Medium | [LeetCode 802](https://leetcode.com/problems/find-eventual-safe-states/) | Reverse topo sort | DFS |
| 4 | Minimum Height Trees | Medium | [LeetCode 310](https://leetcode.com/problems/minimum-height-trees/) | Reverse topo / Centroid | BFS from leaves |
| 5 | Alien Dictionary | Hard (Premium) | [LeetCode 269](https://leetcode.com/problems/alien-dictionary/) | Topological sort | - |
| 6 | Sequence Reconstruction | Medium (Premium) | [LeetCode 444](https://leetcode.com/problems/sequence-reconstruction/) | Unique topo check | - |
| 7 | All Ancestors of a Node in DAG | Medium | [LeetCode 2192](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/) | Topo + sets | DFS |
| 8 | Loud and Rich | Medium | [LeetCode 851](https://leetcode.com/problems/loud-and-rich/) | DFS on DAG | Topo sort |
| 9 | Find All Possible Recipes from Given Supplies | Medium | [LeetCode 2115](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/) | Topo sort | - |
| 10 | Longest Path With Different Adjacent Characters | Hard | [LeetCode 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Tree DP / Topo | DFS |
#### 3.2 Advanced Topological Sort - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 11 | Parallel Courses | Medium (Premium) | [LeetCode 1136](https://leetcode.com/problems/parallel-courses/) | Topo with levels | - |
| 12 | Parallel Courses II | Hard (Premium) | [LeetCode 1494](https://leetcode.com/problems/parallel-courses-ii/) | Topo + bitmask DP | - |
| 13 | Parallel Courses III | Hard | [LeetCode 2050](https://leetcode.com/problems/parallel-courses-iii/) | Topo + DP | - |
| 14 | Sort Items by Groups Respecting Dependencies | Hard | [LeetCode 1203](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/) | Nested topo sort | - |
| 15 | Build a Matrix With Conditions | Hard | [LeetCode 2392](https://leetcode.com/problems/build-a-matrix-with-conditions/) | 2x Topo sort | - |
| 16 | Strange Printer II | Hard | [LeetCode 1591](https://leetcode.com/problems/strange-printer-ii/) | Topo on colors | - |
| 17 | Maximum Employees to Be Invited to a Meeting | Hard | [LeetCode 2127](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/) | Functional graph + topo | DFS |
| 18 | Longest Cycle in a Graph | Hard | [LeetCode 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | Functional graph | - |
| 19 | Count Visited Nodes in a Directed Graph | Hard | [LeetCode 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Functional graph | - |
| 20 | Course Schedule IV | Medium | [LeetCode 1462](https://leetcode.com/problems/course-schedule-iv/) | Topo + reachability | Floyd-Warshall |

### 4. UNION-FIND / DSU - 30 Problems
#### 4.1 Basic DSU Operations - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Find if Path Exists in Graph | Easy | [LeetCode 1971](https://leetcode.com/problems/find-if-path-exists-in-graph/) | Basic connectivity | DFS/BFS |
| 2 | Number of Provinces | Easy | [LeetCode 547](https://leetcode.com/problems/number-of-provinces/) | Count components | DFS/BFS |
| 3 | The Earliest Moment When Everyone Become Friends | Easy (Premium) | [LeetCode 1101](https://leetcode.com/problems/the-earliest-moment-when-everyone-become-friends/) | Time-based union | - |
| 4 | Smallest String With Swaps | Easy | [LeetCode 1202](https://leetcode.com/problems/smallest-string-with-swaps/) | Group by component | - |
| 5 | Redundant Connection | Easy | [LeetCode 684](https://leetcode.com/problems/redundant-connection/) | Cycle detection | DFS |
| 6 | Graph Valid Tree | Medium (Premium) | [LeetCode 261](https://leetcode.com/problems/graph-valid-tree/) | Cycle + connectivity | DFS |
| 7 | Number of Connected Components | Medium (Premium) | [LeetCode 323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/) | Count components | DFS/BFS |
| 8 | Operations to Make Network Connected | Medium | [LeetCode 1319](https://leetcode.com/problems/number-of-operations-to-make-network-connected/) | Component counting | DFS |
| 9 | Sentence Similarity II | Medium (Premium) | [LeetCode 737](https://leetcode.com/problems/sentence-similarity-ii/) | Transitive relation | DFS |
| 10 | Process Restricted Friend Requests | Hard | [LeetCode 2076](https://leetcode.com/problems/process-restricted-friend-requests/) | DSU with constraints | - |
#### 4.2 Grid-Based DSU - 5 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 11 | Regions Cut By Slashes | Medium | [LeetCode 959](https://leetcode.com/problems/regions-cut-by-slashes/) | Grid to DSU (4 parts) | DFS |
| 12 | Number of Islands II | Medium (Premium) | [LeetCode 305](https://leetcode.com/problems/number-of-islands-ii/) | Dynamic connectivity | - |
| 13 | Making a Large Island | Hard | [LeetCode 827](https://leetcode.com/problems/making-a-large-island/) | Size tracking + neighbors | DFS |
| 14 | Surrounded Regions | Medium | [LeetCode 130](https://leetcode.com/problems/surrounded-regions/) | Border-based DSU | DFS/BFS |
| 15 | Count Sub Islands | Medium | [LeetCode 1905](https://leetcode.com/problems/count-sub-islands/) | Grid validation | DFS |
#### 4.3 Advanced DSU Applications - 15 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 16 | Accounts Merge | Medium | [LeetCode 721](https://leetcode.com/problems/accounts-merge/) | Email grouping | DFS |
| 17 | Most Stones Removed with Same Row or Column | Medium | [LeetCode 947](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/) | Total - components | DFS |
| 18 | Satisfiability of Equality Equations | Medium | [LeetCode 990](https://leetcode.com/problems/satisfiability-of-equality-equations/) | Union equals, check inequals | - |
| 19 | Minimize Malware Spread | Medium | [LeetCode 924](https://leetcode.com/problems/minimize-malware-spread/) | Component impact | DFS |
| 20 | Evaluate Division | Medium | [LeetCode 399](https://leetcode.com/problems/evaluate-division/) | Weighted DSU | DFS, Floyd-Warshall |
| 21 | Is Graph Bipartite? | Medium | [LeetCode 785](https://leetcode.com/problems/is-graph-bipartite/) | Bipartite with DSU (2n) | DFS 2-coloring |
| 22 | Possible Bipartition | Medium | [LeetCode 886](https://leetcode.com/problems/possible-bipartition/) | Bipartite DSU | DFS |
| 23 | Lexicographically Smallest Equivalent String | Medium | [LeetCode 1061](https://leetcode.com/problems/lexicographically-smallest-equivalent-string/) | Smallest char as root | - |
| 24 | Checking Existence of Edge Length Limited Paths | Hard | [LeetCode 1697](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/) | Offline queries + DSU | - |
| 25 | Remove Max Number of Edges to Keep Graph Fully Traversable | Hard | [LeetCode 1579](https://leetcode.com/problems/remove-max-number-of-edges-to-keep-graph-fully-traversable/) | Dual DSU | - |
| 26 | Bricks Falling When Hit | Hard | [LeetCode 803](https://leetcode.com/problems/bricks-falling-when-hit/) | Reverse thinking | - |
| 27 | Redundant Connection II | Hard | [LeetCode 685](https://leetcode.com/problems/redundant-connection-ii/) | Directed tree cycle | Complex logic |
| 28 | Number of Good Paths | Hard | [LeetCode 2421](https://leetcode.com/problems/number-of-good-paths/) | Sort + incremental DSU | - |
| 29 | Minimize Hamming Distance After Swap Operations | Medium | [LeetCode 1722](https://leetcode.com/problems/minimize-hamming-distance-after-swap-operations/) | DSU grouping | - |
| 30 | Find All People With Secret | Hard | [LeetCode 2092](https://leetcode.com/problems/find-all-people-with-secret/) | DSU with time | BFS |

### 5. MINIMUM SPANNING TREE (MST) - 12 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Min Cost to Connect All Points | Medium | [LeetCode 1584](https://leetcode.com/problems/min-cost-to-connect-all-points/) | Kruskal's / Prim's | - |
| 2 | Connecting Cities With Minimum Cost | Medium (Premium) | [LeetCode 1135](https://leetcode.com/problems/connecting-cities-with-minimum-cost/) | Kruskal's with DSU | Prim's |
| 3 | Optimize Water Distribution in Village | Hard (Premium) | [LeetCode 1168](https://leetcode.com/problems/optimize-water-distribution-in-a-village/) | MST with virtual node | - |
| 4 | Find Critical and Pseudo-Critical Edges in MST | Hard | [LeetCode 1489](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/) | Kruskal variations | - |
| 5 | Remove Max Number of Edges to Keep Graph Fully Traversable | Hard | [LeetCode 1579](https://leetcode.com/problems/remove-max-number-of-edges-to-keep-graph-fully-traversable/) | Dual MST + DSU | - |
| 6 | Checking Existence of Edge Length Limited Paths | Hard | [LeetCode 1697](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/) | Offline MST + DSU | - |
| 7 | Minimum Cost Walk in Weighted Graph | Hard | [LeetCode 3108](https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/) | DSU with AND | - |
| 8 | Swim in Rising Water | Hard | [LeetCode 778](https://leetcode.com/problems/swim-in-rising-water/) | Binary search + DSU | Dijkstra |
| 9 | Path With Minimum Effort | Medium | [LeetCode 1631](https://leetcode.com/problems/path-with-minimum-effort/) | Binary search + DSU | Dijkstra |
| 10 | Minimize the Total Price of the Trips | Hard | [LeetCode 2646](https://leetcode.com/problems/minimize-the-total-price-of-the-trips/) | Tree DP | - |
| 11 | Count Unreachable Pairs of Nodes | Medium | [LeetCode 2316](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/) | Component sizes | DSU |
| 12 | Divide Nodes Into the Maximum Number of Groups | Hard | [LeetCode 2493](https://leetcode.com/problems/divide-nodes-into-the-maximum-number-of-groups/) | Bipartite + BFS | - |

### 6. CYCLE DETECTION & BIPARTITE - 15 Problems
#### 6.1 Cycle Detection - 8 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Course Schedule | Medium | [LeetCode 207](https://leetcode.com/problems/course-schedule/) | Directed cycle | Topo sort |
| 2 | Redundant Connection | Medium | [LeetCode 684](https://leetcode.com/problems/redundant-connection/) | Undirected cycle | DSU |
| 3 | Redundant Connection II | Hard | [LeetCode 685](https://leetcode.com/problems/redundant-connection-ii/) | Directed tree cycle | DSU + logic |
| 4 | Find Eventual Safe States | Medium | [LeetCode 802](https://leetcode.com/problems/find-eventual-safe-states/) | Cycle detection | Reverse topo |
| 5 | Graph Valid Tree | Medium (Premium) | [LeetCode 261](https://leetcode.com/problems/graph-valid-tree/) | Cycle + connectivity | DSU |
| 6 | Detect Cycles in 2D Grid | Medium | [LeetCode 1559](https://leetcode.com/problems/detect-cycles-in-2d-grid/) | DFS cycle in grid | - |
| 7 | Longest Cycle in a Graph | Hard | [LeetCode 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | Functional graph | - |
| 8 | Count Visited Nodes in a Directed Graph | Hard | [LeetCode 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Functional graph | - |
6.2 Bipartite Graphs - 7 Problems
markdown| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 9 | Is Graph Bipartite? | Medium | [LeetCode 785](https://leetcode.com/problems/is-graph-bipartite/) | DFS 2-coloring | DSU (2n nodes) |
| 10 | Possible Bipartition | Medium | [LeetCode 886](https://leetcode.com/problems/possible-bipartition/) | DFS 2-coloring | DSU |
| 11 | Divide Nodes Into the Maximum Number of Groups | Hard | [LeetCode 2493](https://leetcode.com/problems/divide-nodes-into-the-maximum-number-of-groups/) | Bipartite + BFS | - |
| 12 | Flower Planting With No Adjacent | Medium | [LeetCode 1042](https://leetcode.com/problems/flower-planting-with-no-adjacent/) | Graph coloring (4 colors) | Greedy |
| 13 | Minimum Degree of a Connected Trio in a Graph | Hard | [LeetCode 1761](https://leetcode.com/problems/minimum-degree-of-a-connected-trio-in-a-graph/) | Brute force enumeration | - |
| 14 | Maximum Total Importance of Roads | Medium | [LeetCode 2285](https://leetcode.com/problems/maximum-total-importance-of-roads/) | Greedy degree sort | - |
| 15 | Escape the Spreading Fire | Hard | [LeetCode 2258](https://leetcode.com/problems/escape-the-spreading-fire/) | Binary search + BFS | - |

### 7. ARTICULATION POINTS & BRIDGES - 8 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Critical Connections in a Network | Hard | [LeetCode 1192](https://leetcode.com/problems/critical-connections-in-a-network/) | Tarjan's (bridges) | - |
| 2 | Minimum Number of Days to Disconnect Island | Hard | [LeetCode 1568](https://leetcode.com/problems/minimum-number-of-days-to-disconnect-island/) | Articulation points | Brute force |
| 3 | Find Servers That Handled Most Requests | Medium | [LeetCode 1606](https://leetcode.com/problems/find-servers-that-handled-most-number-of-requests/) | Simulation | - |
| 4 | Maximum Number of Fish in a Grid | Medium | [LeetCode 2658](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/) | DFS/BFS | DSU |
| 5 | Number of Enclaves | Medium | [LeetCode 1020](https://leetcode.com/problems/number-of-enclaves/) | Border DFS | - |
| 6 | Count Unreachable Pairs of Nodes | Medium | [LeetCode 2316](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/) | Component sizes | DSU |
| 7 | Minimize the Total Price of the Trips | Hard | [LeetCode 2646](https://leetcode.com/problems/minimize-the-total-price-of-the-trips/) | Tree DP | - |
| 8 | Closest Node to Path in Tree | Hard (Premium) | [LeetCode 2277](https://leetcode.com/problems/closest-node-to-path-in-tree/) | LCA + distance | - |

### 8. TREE ALGORITHMS - 30 Problems
#### 8.1 Basic Tree Traversal - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Maximum Depth of Binary Tree | Easy | [LeetCode 104](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | DFS/BFS | - |
| 2 | Minimum Depth of Binary Tree | Easy | [LeetCode 111](https://leetcode.com/problems/minimum-depth-of-binary-tree/) | DFS/BFS | - |
| 3 | Diameter of Binary Tree | Easy | [LeetCode 543](https://leetcode.com/problems/diameter-of-binary-tree/) | Tree DP | - |
| 4 | Binary Tree Right Side View | Medium | [LeetCode 199](https://leetcode.com/problems/binary-tree-right-side-view/) | BFS level order | DFS |
| 5 | Count Good Nodes in Binary Tree | Medium | [LeetCode 1448](https://leetcode.com/problems/count-good-nodes-in-binary-tree/) | DFS with max | - |
| 6 | Maximum Difference Between Node and Ancestor | Medium | [LeetCode 1026](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/) | DFS with min/max | - |
| 7 | Delete Nodes And Return Forest | Medium | [LeetCode 1110](https://leetcode.com/problems/delete-nodes-and-return-forest/) | DFS | - |
| 8 | Binary Tree Coloring Game | Medium | [LeetCode 1145](https://leetcode.com/problems/binary-tree-coloring-game/) | Tree size calc | - |
| 9 | Create Binary Tree From Descriptions | Medium | [LeetCode 2196](https://leetcode.com/problems/create-binary-tree-from-descriptions/) | HashMap | - |
| 10 | Recover a Tree From Preorder Traversal | Hard | [LeetCode 1028](https://leetcode.com/problems/recover-a-tree-from-preorder-traversal/) | Stack | Recursion |
#### 8.2 Tree DP & Path Problems - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 11 | Binary Tree Maximum Path Sum | Hard | [LeetCode 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | Tree DP | - |
| 12 | House Robber III | Medium | [LeetCode 337](https://leetcode.com/problems/house-robber-iii/) | Tree DP | - |
| 13 | Binary Tree Cameras | Hard | [LeetCode 968](https://leetcode.com/problems/binary-tree-cameras/) | Tree DP (greedy) | - |
| 14 | Distribute Coins in Binary Tree | Medium | [LeetCode 979](https://leetcode.com/problems/distribute-coins-in-binary-tree/) | Tree DFS | - |
| 15 | Longest Univalue Path | Medium | [LeetCode 687](https://leetcode.com/problems/longest-univalue-path/) | Tree DP | - |
| 16 | Count Nodes Equal to Average of Subtree | Medium | [LeetCode 2265](https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/) | Tree DFS | - |
| 17 | Maximum Product of Splitted Binary Tree | Medium | [LeetCode 1339](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/) | Tree DFS | - |
| 18 | Linked List in Binary Tree | Medium | [LeetCode 1367](https://leetcode.com/problems/linked-list-in-binary-tree/) | DFS matching | KMP |
| 19 | Smallest Subtree with all the Deepest Nodes | Medium | [LeetCode 865](https://leetcode.com/problems/smallest-subtree-with-all-the-deepest-nodes/) | DFS depth | - |
| 20 | Minimum Score After Removals on a Tree | Hard | [LeetCode 2538](https://leetcode.com/problems/minimum-score-after-removals-on-a-tree/) | Tree DFS + XOR | - |
#### 8.3 LCA & Advanced Tree - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 21 | Lowest Common Ancestor of a Binary Tree | Medium | [LeetCode 236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | DFS | Binary lifting |
| 22 | Kth Ancestor of a Tree Node | Hard | [LeetCode 1483](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) | Binary lifting | Jump pointers |
| 23 | Sum of Distances in Tree | Hard | [LeetCode 834](https://leetcode.com/problems/sum-of-distances-in-tree/) | Tree DP (reroot) | - |
| 24 | All Nodes Distance K in Binary Tree | Medium | [LeetCode 863](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/) | BFS with parents | DFS |
| 25 | Amount of Time for Binary Tree to Be Infected | Medium | [LeetCode 2385](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/) | BFS/DFS | - |
| 26 | Step-By-Step Directions From Binary Tree Node to Another | Medium | [LeetCode 2096](https://leetcode.com/problems/step-by-step-directions-from-a-binary-tree-node-to-another/) | LCA + path | - |
| 27 | Closest Node to Path in Tree | Hard (Premium) | [LeetCode 2277](https://leetcode.com/problems/closest-node-to-path-in-tree/) | LCA + distance | - |
| 28 | Minimum Fuel Cost to Report to the Capital | Medium | [LeetCode 2477](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/) | Tree DFS | - |
| 29 | Maximum Number of K-Divisible Components | Hard | [LeetCode 2872](https://leetcode.com/problems/maximum-number-of-k-divisible-components/) | Tree DFS | - |
| 30 | Longest Path With Different Adjacent Characters | Hard | [LeetCode 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Tree DP | - |

### 9. ADVANCED BFS/STATE SEARCH - 15 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Snakes and Ladders | Medium | [LeetCode 909](https://leetcode.com/problems/snakes-and-ladders/) | BFS | - |
| 2 | Bus Routes | Hard | [LeetCode 815](https://leetcode.com/problems/bus-routes/) | BFS on buses | - |
| 3 | Sliding Puzzle | Hard | [LeetCode 773](https://leetcode.com/problems/sliding-puzzle/) | BFS state space | A* |
| 4 | Minimum Moves to Move a Box to Target | Hard | [LeetCode 1263](https://leetcode.com/problems/minimum-moves-to-move-a-box-to-their-target-location/) | BFS 2 states | A* |
| 5 | Jump Game IV | Hard | [LeetCode 1345](https://leetcode.com/problems/jump-game-iv/) | BFS with optimization | - |
| 6 | Minimum Jumps to Reach Home | Medium | [LeetCode 1654](https://leetcode.com/problems/minimum-jumps-to-reach-home/) | BFS with constraints | - |
| 7 | Race Car | Hard | [LeetCode 818](https://leetcode.com/problems/race-car/) | BFS/DP | - |
| 8 | K-Similar Strings | Hard | [LeetCode 854](https://leetcode.com/problems/k-similar-strings/) | BFS permutation | - |
| 9 | Shortest Path to Get All Keys | Hard | [LeetCode 864](https://leetcode.com/problems/shortest-path-to-get-all-keys/) | BFS bitmask | Dijkstra |
| 10 | Shortest Path Visiting All Nodes | Hard | [LeetCode 847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) | BFS bitmask | Dijkstra |
| 11 | Shortest Path in Grid with Obstacles Elimination | Hard | [LeetCode 1293](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/) | BFS with state | A* |
| 12 | Minimum Reverse Operations | Hard | [LeetCode 2612](https://leetcode.com/problems/minimum-reverse-operations/) | BFS + DSU | - |
| 13 | Escape the Spreading Fire | Hard | [LeetCode 2258](https://leetcode.com/problems/escape-the-spreading-fire/) | Binary search + BFS | - |
| 14 | Find Minimum Time to Finish All Jobs | Hard | [LeetCode 1723](https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/) | Backtracking + pruning | Binary search + DP |
| 15 | Reconstruct Itinerary | Hard | [LeetCode 332](https://leetcode.com/problems/reconstruct-itinerary/) | DFS Eulerian path | Hierholzer's |

### 10. SPECIAL GRAPH PROBLEMS - 10 Problems
| # | Problem Name | Difficulty | Link | Key Concept | Alternative Approaches |
|---|--------------|------------|------|-------------|------------------------|
| 1 | Evaluate Division | Medium | [LeetCode 399](https://leetcode.com/problems/evaluate-division/) | DFS / Weighted DSU | Floyd-Warshall |
| 2 | Reconstruct Itinerary | Hard | [LeetCode 332](https://leetcode.com/problems/reconstruct-itinerary/) | Eulerian path | Hierholzer's |
| 3 | Maximum Employees to Be Invited to a Meeting | Hard | [LeetCode 2127](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/) | Functional graph | Topo + cycle |
| 4 | Longest Cycle in a Graph | Hard | [LeetCode 2360](https://leetcode.com/problems/longest-cycle-in-a-graph/) | Functional graph | - |
| 5 | Count Visited Nodes in a Directed Graph | Hard | [LeetCode 2876](https://leetcode.com/problems/count-visited-nodes-in-a-directed-graph/) | Functional graph | - |
| 6 | Minimum Number of K Consecutive Bit Flips | Hard | [LeetCode 995](https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips/) | Greedy + diff array | - |
| 7 | Checking Existence of Edge Length Limited Paths II | Hard | [LeetCode 2846](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths-ii/) | Persistent DSU | - |
| 8 | Find All People With Secret | Hard | [LeetCode 2092](https://leetcode.com/problems/find-all-people-with-secret/) | DSU with time | BFS |
| 9 | Minimum Cost Walk in Weighted Graph | Hard | [LeetCode 3108](https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/) | DSU with AND | - |
| 10 | Modify Graph Edge Weights | Hard | [LeetCode 2699](https://leetcode.com/problems/modify-graph-edge-weights/) | Dijkstra + construction | - |


