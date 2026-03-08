# 🧠 DYNAMIC PROGRAMMING — Complete Problem Sheet
> Covers all DP topics from Beginner to Expert | ~200 Problems | LeetCode + GFG

---

## 1. 1D LINEAR DP
### 1.1 Fibonacci & Basic Patterns (Easy)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Fibonacci Number | Easy | [LC 509](https://leetcode.com/problems/fibonacci-number/) | Memoization / Tabulation | Math formula |
| 2 | Climbing Stairs | Easy | [LC 70](https://leetcode.com/problems/climbing-stairs/) | Fibonacci pattern | Matrix exponentiation |
| 3 | Min Cost Climbing Stairs | Easy | [LC 746](https://leetcode.com/problems/min-cost-climbing-stairs/) | Bottom-up 1D DP | - |
| 4 | N-th Tribonacci Number | Easy | [LC 1137](https://leetcode.com/problems/n-th-tribonacci-number/) | 3-state Fibonacci | - |
| 5 | Domino and Tromino Tiling | Medium | [LC 790](https://leetcode.com/problems/domino-and-tromino-tiling/) | State transition | - |
| 6 | Count Ways to Reach nth Stair | Easy | [GFG](https://www.geeksforgeeks.org/count-ways-reach-nth-stair/) | Fibonacci | - |
| 7 | Frog Jump (1 or 2 steps) | Easy | [GFG](https://www.geeksforgeeks.org/count-number-of-ways-to-cover-a-distance/) | 1D DP | - |
| 8 | Minimum Jumps | Medium | [GFG](https://www.geeksforgeeks.org/minimum-number-of-jumps-to-reach-end-of-a-given-array/) | DP / Greedy | - |

### 1.2 House Robber & Variants (Easy-Medium)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 9 | House Robber | Medium | [LC 198](https://leetcode.com/problems/house-robber/) | Non-adjacent selection | - |
| 10 | House Robber II | Medium | [LC 213](https://leetcode.com/problems/house-robber-ii/) | Circular array | - |
| 11 | House Robber III | Medium | [LC 337](https://leetcode.com/problems/house-robber-iii/) | Tree DP | - |
| 12 | House Robber IV | Medium | [LC 2560](https://leetcode.com/problems/house-robber-iv/) | Binary search + DP | - |
| 13 | Delete and Earn | Medium | [LC 740](https://leetcode.com/problems/delete-and-earn/) | Transform to House Robber | - |

### 1.3 Subarray / Subsequence 1D (Easy-Medium)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 14 | Maximum Subarray | Medium | [LC 53](https://leetcode.com/problems/maximum-subarray/) | Kadane's Algorithm | Divide & Conquer |
| 15 | Maximum Sum Circular Subarray | Medium | [LC 918](https://leetcode.com/problems/maximum-sum-circular-subarray/) | Kadane's variant | - |
| 16 | Maximum Product Subarray | Medium | [LC 152](https://leetcode.com/problems/maximum-product-subarray/) | Track min & max | - |
| 17 | Longest Turbulent Subarray | Medium | [LC 978](https://leetcode.com/problems/longest-turbulent-subarray/) | 2-state DP | Sliding window |
| 18 | Maximum Length of Repeated Subarray | Medium | [LC 718](https://leetcode.com/problems/maximum-length-of-repeated-subarray/) | 2D DP | - |
| 19 | Arithmetic Slices | Medium | [LC 413](https://leetcode.com/problems/arithmetic-slices/) | Incremental DP | - |
| 20 | Number of Arithmetic Triplets | Easy | [LC 2367](https://leetcode.com/problems/number-of-arithmetic-triplets/) | HashMap DP | - |
| 21 | Arithmetic Slices II - Subsequence | Hard | [LC 446](https://leetcode.com/problems/arithmetic-slices-ii-subsequence/) | HashMap DP (count) | - |

### 1.4 Decode & Partition Strings (Medium)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 22 | Decode Ways | Medium | [LC 91](https://leetcode.com/problems/decode-ways/) | 1D DP with constraints | - |
| 23 | Decode Ways II | Hard | [LC 639](https://leetcode.com/problems/decode-ways-ii/) | Extended decode DP | - |
| 24 | Word Break | Medium | [LC 139](https://leetcode.com/problems/word-break/) | 1D DP + set | BFS, Trie |
| 25 | Word Break II | Hard | [LC 140](https://leetcode.com/problems/word-break-ii/) | Backtracking + memo | - |
| 26 | Perfect Squares | Medium | [LC 279](https://leetcode.com/problems/perfect-squares/) | Coin change pattern | BFS, Math |
| 27 | Minimum Cost For Tickets | Medium | [LC 983](https://leetcode.com/problems/minimum-cost-for-tickets/) | 1D DP on days | - |

---

## 2. KNAPSACK DP
### 2.1 0/1 Knapsack — Core Problems (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | 0/1 Knapsack Problem | Medium | [GFG](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/) | Classic 0/1 Knapsack | - |
| 2 | Subset Sum Problem | Medium | [GFG](https://www.geeksforgeeks.org/subset-sum-problem-dp-25/) | Boolean DP | - |
| 3 | Partition Equal Subset Sum | Medium | [LC 416](https://leetcode.com/problems/partition-equal-subset-sum/) | Subset sum variant | - |
| 4 | Target Sum | Medium | [LC 494](https://leetcode.com/problems/target-sum/) | Count subsets | DFS+memo |
| 5 | Last Stone Weight II | Medium | [LC 1049](https://leetcode.com/problems/last-stone-weight-ii/) | Min subset diff | - |
| 6 | Ones and Zeroes | Medium | [LC 474](https://leetcode.com/problems/ones-and-zeroes/) | 2D knapsack | - |
| 7 | Minimum Subset Sum Difference | Medium | [GFG](https://www.geeksforgeeks.org/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum/) | Subset sum extension | - |
| 8 | Count Subsets with Given Sum | Medium | [GFG](https://www.geeksforgeeks.org/count-of-subsets-with-sum-equal-to-x/) | Counting variant | - |
| 9 | Count Subsets with Given Difference | Medium | [GFG](https://www.geeksforgeeks.org/number-of-subsets-with-given-difference/) | Derived from subset sum | - |
| 10 | Profitable Schemes | Hard | [LC 879](https://leetcode.com/problems/profitable-schemes/) | 3D knapsack | - |

### 2.2 Unbounded Knapsack (Medium)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 11 | Unbounded Knapsack | Medium | [GFG](https://www.geeksforgeeks.org/unbounded-knapsack-repetition-items-allowed/) | Unlimited items | - |
| 12 | Coin Change (Min Coins) | Medium | [LC 322](https://leetcode.com/problems/coin-change/) | Unbounded Knapsack | BFS |
| 13 | Coin Change II (Count Ways) | Medium | [LC 518](https://leetcode.com/problems/coin-change-ii/) | Unbounded count | - |
| 14 | Integer Break | Medium | [LC 343](https://leetcode.com/problems/integer-break/) | Rod cutting variant | Math |
| 15 | Rod Cutting | Medium | [GFG](https://www.geeksforgeeks.org/cutting-a-rod-dp-13/) | Classic unbounded | - |
| 16 | Minimum Ribbon Cut | Medium | [GFG](https://www.geeksforgeeks.org/minimum-cuts-ribbon/) | Unbounded with constraint | - |
| 17 | Maximum Ribbon Cut | Medium | [GFG](https://www.geeksforgeeks.org/maximum-number-of-pieces-of-given-lengths/) | Unbounded variant | - |

### 2.3 Multi-Dimensional Knapsack (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 18 | Shopping Offers | Medium | [LC 638](https://leetcode.com/problems/shopping-offers/) | State DP | DFS+memo |
| 19 | Find the Minimum and Maximum Number of Nodes Between Critical Points | Medium | [LC 2058](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/) | - | - |
| 20 | Maximum Profit in Job Scheduling | Hard | [LC 1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/) | Binary search + DP | Segment tree |
| 21 | Minimum Difficulty of a Job Schedule | Hard | [LC 1335](https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/) | DP with partition | - |
| 22 | K Inverse Pairs Array | Hard | [LC 629](https://leetcode.com/problems/k-inverse-pairs-array/) | 2D DP with prefix sum | - |

---

## 3. STRING DP
### 3.1 Longest Common Subsequence (LCS) Variants (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Longest Common Subsequence | Medium | [LC 1143](https://leetcode.com/problems/longest-common-subsequence/) | Classic LCS | - |
| 2 | Longest Common Substring | Medium | [GFG](https://www.geeksforgeeks.org/longest-common-substring-dp-29/) | LCS variant (contiguous) | - |
| 3 | Print LCS | Medium | [GFG](https://www.geeksforgeeks.org/printing-longest-common-subsequence/) | LCS reconstruction | - |
| 4 | Shortest Common Supersequence | Hard | [LC 1092](https://leetcode.com/problems/shortest-common-supersequence/) | LCS + reconstruction | - |
| 5 | Delete Operations for Two Strings | Medium | [LC 583](https://leetcode.com/problems/delete-operation-for-two-strings/) | LCS length use | - |
| 6 | Minimum ASCII Delete Sum | Medium | [LC 712](https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings/) | Weighted LCS | - |
| 7 | Longest Repeating Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/longest-repeating-subsequence/) | LCS(s,s) with constraint | - |
| 8 | Sequence Pattern Matching | Easy | [GFG](https://www.geeksforgeeks.org/given-two-strings-find-first-string-subsequence-second/) | Check LCS = s1 | - |
| 9 | Maximum Length of Repeated Subarray | Medium | [LC 718](https://leetcode.com/problems/maximum-length-of-repeated-subarray/) | LCS contiguous | Binary search + hash |
| 10 | Uncrossed Lines | Medium | [LC 1035](https://leetcode.com/problems/uncrossed-lines/) | LCS disguised | - |

### 3.2 Longest Increasing Subsequence (LIS) Variants (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 11 | Longest Increasing Subsequence | Medium | [LC 300](https://leetcode.com/problems/longest-increasing-subsequence/) | DP O(n²) / Patience sort O(n log n) | Binary search |
| 12 | Number of Longest Increasing Subsequences | Medium | [LC 673](https://leetcode.com/problems/number-of-longest-increasing-subsequence/) | Count + DP | - |
| 13 | Print LIS | Medium | [GFG](https://www.geeksforgeeks.org/construction-of-longest-increasing-subsequence-using-dynamic-programming/) | LIS reconstruction | - |
| 14 | Largest Divisible Subset | Medium | [LC 368](https://leetcode.com/problems/largest-divisible-subset/) | LIS variant with divisibility | - |
| 15 | Russian Doll Envelopes | Hard | [LC 354](https://leetcode.com/problems/russian-doll-envelopes/) | 2D LIS | Binary search |
| 16 | Longest Bitonic Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/longest-bitonic-subsequence-dp-15/) | LIS + LDS | - |
| 17 | Maximum Sum Increasing Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/maximum-sum-increasing-subsequence-dp-14/) | LIS with sum | - |
| 18 | Minimum Number of Removals to Make Mountain Array | Hard | [LC 1671](https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/) | Bitonic LIS | - |
| 19 | Make Array Strictly Increasing | Hard | [LC 1187](https://leetcode.com/problems/make-array-strictly-increasing/) | LIS + binary search | - |
| 20 | Box Stacking Problem | Hard | [GFG](https://www.geeksforgeeks.org/box-stacking-problem-dp-22/) | 3D LIS | - |

### 3.3 Edit Distance & Matching (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 21 | Edit Distance | Hard | [LC 72](https://leetcode.com/problems/edit-distance/) | Classic DP | - |
| 22 | One Edit Distance | Medium (Premium) | [LC 161](https://leetcode.com/problems/one-edit-distance/) | Edit distance = 1 | - |
| 23 | Wildcard Matching | Hard | [LC 44](https://leetcode.com/problems/wildcard-matching/) | 2D DP with * and ? | - |
| 24 | Regular Expression Matching | Hard | [LC 10](https://leetcode.com/problems/regular-expression-matching/) | 2D DP with * and . | - |
| 25 | Interleaving String | Medium | [LC 97](https://leetcode.com/problems/interleaving-string/) | 2D DP | DFS+memo |
| 26 | Distinct Subsequences | Hard | [LC 115](https://leetcode.com/problems/distinct-subsequences/) | Count subsequences | - |
| 27 | Is Subsequence | Easy | [LC 392](https://leetcode.com/problems/is-subsequence/) | Two pointers / DP | - |
| 28 | Number of Matching Subsequences | Medium | [LC 792](https://leetcode.com/problems/number-of-matching-subsequences/) | Map + DP | - |
| 29 | Minimum Insertions to Make String Palindrome | Hard | [LC 1312](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/) | LCS variant | - |
| 30 | Longest Palindromic Subsequence | Medium | [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/) | LCS(s, rev_s) | - |

### 3.4 Palindrome DP (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 31 | Longest Palindromic Substring | Medium | [LC 5](https://leetcode.com/problems/longest-palindromic-substring/) | Expand around center / DP | Manacher's |
| 32 | Palindromic Substrings (Count) | Medium | [LC 647](https://leetcode.com/problems/palindromic-substrings/) | Expand / DP | Manacher's |
| 33 | Palindrome Partitioning | Medium | [LC 131](https://leetcode.com/problems/palindrome-partitioning/) | Backtracking + DP | - |
| 34 | Palindrome Partitioning II (Min Cuts) | Hard | [LC 132](https://leetcode.com/problems/palindrome-partitioning-ii/) | DP for palindrome precompute | - |
| 35 | Palindrome Partitioning III | Hard | [LC 1278](https://leetcode.com/problems/palindrome-partitioning-iii/) | 2D DP | - |
| 36 | Count Different Palindromic Subsequences | Hard | [LC 730](https://leetcode.com/problems/count-different-palindromic-subsequences/) | Interval DP | - |
| 37 | Count Palindromic Subsequences | Hard | [LC 2484](https://leetcode.com/problems/count-palindromic-subsequences/) | DP | - |

---

## 4. GRID / 2D DP
### 4.1 Grid Path Problems (Easy-Medium)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Unique Paths | Medium | [LC 62](https://leetcode.com/problems/unique-paths/) | 2D DP / Combinatorics | Math |
| 2 | Unique Paths II (Obstacles) | Medium | [LC 63](https://leetcode.com/problems/unique-paths-ii/) | 2D DP with blocked cells | - |
| 3 | Minimum Path Sum | Medium | [LC 64](https://leetcode.com/problems/minimum-path-sum/) | 2D DP | - |
| 4 | Triangle | Medium | [LC 120](https://leetcode.com/problems/triangle/) | 1D DP bottom-up | - |
| 5 | Minimum Falling Path Sum | Medium | [LC 931](https://leetcode.com/problems/minimum-falling-path-sum/) | 2D DP | - |
| 6 | Minimum Falling Path Sum II | Hard | [LC 1289](https://leetcode.com/problems/minimum-falling-path-sum-ii/) | DP + track 2 min | - |
| 7 | Dungeon Game | Hard | [LC 174](https://leetcode.com/problems/dungeon-game/) | Reverse 2D DP | - |
| 8 | Gold Mine Problem | Medium | [GFG](https://www.geeksforgeeks.org/gold-mine-problem/) | 2D DP | - |
| 9 | Count All Paths in Grid | Easy | [GFG](https://www.geeksforgeeks.org/count-possible-paths-top-left-bottom-right-nxm-matrix/) | Basic 2D DP | - |
| 10 | Minimum Path Cost in a Grid | Medium | [LC 2304](https://leetcode.com/problems/minimum-path-cost-in-a-grid/) | 2D DP with transition cost | - |

### 4.2 Grid Rectangle / Square Problems (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 11 | Maximal Square | Medium | [LC 221](https://leetcode.com/problems/maximal-square/) | 2D DP for max square | - |
| 12 | Count Square Submatrices with All Ones | Medium | [LC 1277](https://leetcode.com/problems/count-square-submatrices-with-all-ones/) | Maximal square variant | - |
| 13 | Maximal Rectangle | Hard | [LC 85](https://leetcode.com/problems/maximal-rectangle/) | Histogram DP | Stack |
| 14 | Number of Submatrices That Sum to Target | Hard | [LC 1074](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/) | Prefix sum 2D | - |
| 15 | Matrix Block Sum | Medium | [LC 1314](https://leetcode.com/problems/matrix-block-sum/) | 2D prefix sum | - |

### 4.3 Multi-State Grid DP (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 16 | Cherry Pickup | Hard | [LC 741](https://leetcode.com/problems/cherry-pickup/) | 2 agents on grid | - |
| 17 | Cherry Pickup II | Hard | [LC 1463](https://leetcode.com/problems/cherry-pickup-ii/) | 2 agents top-down | - |
| 18 | Out of Boundary Paths | Medium | [LC 576](https://leetcode.com/problems/out-of-boundary-paths/) | DP count paths | DFS+memo |
| 19 | Number of Paths with Max Score | Hard | [LC 1301](https://leetcode.com/problems/number-of-paths-with-max-score/) | 2D DP (max + count) | - |
| 20 | Longest Increasing Path in a Matrix | Hard | [LC 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | DFS + memo | Topo sort |

---

## 5. INTERVAL DP
### 5.1 Classic Interval DP (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Matrix Chain Multiplication | Hard | [GFG](https://www.geeksforgeeks.org/matrix-chain-multiplication-dp-8/) | Classic interval DP | - |
| 2 | Burst Balloons | Hard | [LC 312](https://leetcode.com/problems/burst-balloons/) | Reverse thinking interval DP | - |
| 3 | Strange Printer | Hard | [LC 664](https://leetcode.com/problems/strange-printer/) | Interval DP | - |
| 4 | Remove Boxes | Hard | [LC 546](https://leetcode.com/problems/remove-boxes/) | Interval DP with state | - |
| 5 | Minimum Cost to Merge Stones | Hard | [LC 1000](https://leetcode.com/problems/minimum-cost-to-merge-stones/) | Interval DP | - |
| 6 | Optimal Binary Search Tree | Hard | [GFG](https://www.geeksforgeeks.org/optimal-binary-search-tree-dp-24/) | Interval DP (weighted) | - |
| 7 | Zuma Game | Hard | [LC 488](https://leetcode.com/problems/zuma-game/) | Interval DP | - |
| 8 | Minimum Score Triangulation of Polygon | Medium | [LC 1039](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/) | Interval DP | - |
| 9 | Strange Printer II | Hard | [LC 1591](https://leetcode.com/problems/strange-printer-ii/) | Topological sort + DP | - |
| 10 | Minimum Cost to Cut a Stick | Hard | [LC 1547](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/) | Interval DP (like MCM) | - |

### 5.2 Game Theory / Picking Problems (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 11 | Predict the Winner | Medium | [LC 486](https://leetcode.com/problems/predict-the-winner/) | Minimax DP | - |
| 12 | Stone Game | Medium | [LC 877](https://leetcode.com/problems/stone-game/) | Interval DP / Math | - |
| 13 | Stone Game II | Medium | [LC 1140](https://leetcode.com/problems/stone-game-ii/) | DP with variable M | - |
| 14 | Stone Game III | Hard | [LC 1406](https://leetcode.com/problems/stone-game-iii/) | DP with lookahead | - |
| 15 | Stone Game IV | Hard | [LC 1510](https://leetcode.com/problems/stone-game-iv/) | DP on square numbers | - |
| 16 | Stone Game V | Hard | [LC 1563](https://leetcode.com/problems/stone-game-v/) | Interval DP | - |
| 17 | Stone Game VII | Medium | [LC 1690](https://leetcode.com/problems/stone-game-vii/) | Interval DP | - |
| 18 | Stone Game VIII | Hard | [LC 1872](https://leetcode.com/problems/stone-game-viii/) | Suffix DP | - |
| 19 | Guess Number Higher or Lower II | Medium | [LC 375](https://leetcode.com/problems/guess-number-higher-or-lower-ii/) | Minimax DP | - |
| 20 | Can I Win | Medium | [LC 464](https://leetcode.com/problems/can-i-win/) | Bitmask + memo | - |

---

## 6. PARTITION DP
### 6.1 Array Partition Problems (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Partition Array for Maximum Sum | Medium | [LC 1043](https://leetcode.com/problems/partition-array-for-maximum-sum/) | DP with window | - |
| 2 | Largest Sum of Averages | Medium | [LC 813](https://leetcode.com/problems/largest-sum-of-averages/) | DP + prefix sum | - |
| 3 | Split Array Largest Sum | Hard | [LC 410](https://leetcode.com/problems/split-array-largest-sum/) | DP / Binary search | - |
| 4 | Painters Partition Problem | Hard | [GFG](https://www.geeksforgeeks.org/painters-partition-problem/) | Binary search + DP | - |
| 5 | Allocate Minimum Number of Pages | Hard | [GFG](https://www.geeksforgeeks.org/allocate-minimum-number-pages/) | Binary search + greedy | - |
| 6 | Minimum Cost to Partition Array | Hard | [LC 2369](https://leetcode.com/problems/check-if-there-is-a-valid-partition-for-the-array/) | DP | - |
| 7 | Check if There is a Valid Partition | Medium | [LC 2369](https://leetcode.com/problems/check-if-there-is-a-valid-partition-for-the-array/) | 1D DP | - |
| 8 | Minimum Number of Operations to Make Array Continuous | Hard | [LC 2009](https://leetcode.com/problems/minimum-number-of-operations-to-make-array-continuous/) | Sliding window + DP | - |

### 6.2 Egg Drop & Classic Hard Partitions (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 9 | Egg Drop Problem | Hard | [GFG](https://www.geeksforgeeks.org/egg-dropping-puzzle-dp-11/) | Classic 2D DP | - |
| 10 | Super Egg Drop | Hard | [LC 887](https://leetcode.com/problems/super-egg-drop/) | DP + binary search | Math |
| 11 | Frog Jump | Hard | [LC 403](https://leetcode.com/problems/frog-jump/) | DP with set of jumps | - |
| 12 | Jump Game VI | Medium | [LC 1696](https://leetcode.com/problems/jump-game-vi/) | DP + deque | Segment tree |
| 13 | Jump Game VII | Medium | [LC 1871](https://leetcode.com/problems/jump-game-vii/) | DP + prefix sum | - |

---

## 7. STOCK MARKET DP (State Machine)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Best Time to Buy & Sell Stock I | Easy | [LC 121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) | One transaction | Greedy |
| 2 | Best Time to Buy & Sell Stock II | Medium | [LC 122](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) | Unlimited transactions | Greedy |
| 3 | Best Time to Buy & Sell Stock III | Hard | [LC 123](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) | At most 2 transactions | - |
| 4 | Best Time to Buy & Sell Stock IV | Hard | [LC 188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) | At most k transactions | - |
| 5 | Best Time to Buy & Sell Stock with Cooldown | Medium | [LC 309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) | State machine DP | - |
| 6 | Best Time to Buy & Sell Stock with Transaction Fee | Medium | [LC 714](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/) | State machine DP | - |
| 7 | Maximum Profit from Trading Stocks (GFG) | Medium | [GFG](https://www.geeksforgeeks.org/stock-buy-sell/) | General k transactions | - |

---

## 8. TREE DP
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Diameter of Binary Tree | Easy | [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/) | Tree DP | - |
| 2 | Binary Tree Maximum Path Sum | Hard | [LC 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | Tree DP | - |
| 3 | House Robber III | Medium | [LC 337](https://leetcode.com/problems/house-robber-iii/) | Tree DP (rob/not rob) | - |
| 4 | Binary Tree Cameras | Hard | [LC 968](https://leetcode.com/problems/binary-tree-cameras/) | 3-state Tree DP | - |
| 5 | Distribute Coins in Binary Tree | Medium | [LC 979](https://leetcode.com/problems/distribute-coins-in-binary-tree/) | Tree DFS | - |
| 6 | Maximum Product of Splitted Binary Tree | Medium | [LC 1339](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/) | Prefix subtree sum | - |
| 7 | Longest Univalue Path | Medium | [LC 687](https://leetcode.com/problems/longest-univalue-path/) | Tree DP | - |
| 8 | Sum of Distances in Tree | Hard | [LC 834](https://leetcode.com/problems/sum-of-distances-in-tree/) | Tree DP (reroot) | - |
| 9 | Minimum Cost Tree from Leaf Values | Medium | [LC 1130](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/) | DP / Monotone stack | - |
| 10 | Longest Path with Different Adjacent Chars | Hard | [LC 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Tree DP | - |
| 11 | Count Nodes Equal to Average of Subtree | Medium | [LC 2265](https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/) | Tree DFS | - |
| 12 | Minimum Score After Removals on a Tree | Hard | [LC 2538](https://leetcode.com/problems/minimum-score-after-removals-on-a-tree/) | XOR + DFS in/out | - |
| 13 | Maximum Number of K-Divisible Components | Hard | [LC 2872](https://leetcode.com/problems/maximum-number-of-k-divisible-components/) | Tree DFS | - |
| 14 | Minimize the Total Price of Trips | Hard | [LC 2646](https://leetcode.com/problems/minimize-the-total-price-of-the-trips/) | Tree DP (rob style) | - |
| 15 | All Possible Full Binary Trees | Medium | [LC 894](https://leetcode.com/problems/all-possible-full-binary-trees/) | Tree DP (count) | - |

---

## 9. BITMASK DP
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Travelling Salesman Problem | Hard | [GFG](https://www.geeksforgeeks.org/travelling-salesman-problem-set-1/) | Classic bitmask DP | - |
| 2 | Shortest Path Visiting All Nodes | Hard | [LC 847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) | BFS + bitmask | - |
| 3 | Find Minimum Time to Finish All Jobs | Hard | [LC 1723](https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/) | Bitmask DP | Backtracking |
| 4 | Smallest Sufficient Team | Hard | [LC 1125](https://leetcode.com/problems/smallest-sufficient-team/) | Bitmask DP | - |
| 5 | Parallel Courses II | Hard | [LC 1494](https://leetcode.com/problems/parallel-courses-ii/) | Bitmask DP + topo | - |
| 6 | Maximum Students Taking Exam | Hard | [LC 1349](https://leetcode.com/problems/maximum-students-taking-exam/) | Bitmask DP (row by row) | - |
| 7 | Number of Ways to Wear Different Hats | Hard | [LC 1434](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/) | Bitmask DP | - |
| 8 | Stickers to Spell Word | Hard | [LC 691](https://leetcode.com/problems/stickers-to-spell-word/) | Bitmask DP | - |
| 9 | Minimum XOR Sum of Two Arrays | Hard | [LC 1879](https://leetcode.com/problems/minimum-xor-sum-of-two-arrays/) | Bitmask DP | Hungarian alg |
| 10 | Maximum AND Sum of Array | Hard | [LC 2172](https://leetcode.com/problems/maximum-and-sum-of-array/) | Bitmask DP | - |
| 11 | Distribute Repeating Integers | Hard | [LC 1655](https://leetcode.com/problems/distribute-repeating-integers/) | Bitmask DP | - |
| 12 | Number of Squareful Arrays | Hard | [LC 996](https://leetcode.com/problems/number-of-squareful-arrays/) | Bitmask DP / Backtracking | - |
| 13 | Maximize Score After N Operations | Hard | [LC 1799](https://leetcode.com/problems/maximize-score-after-n-operations/) | Bitmask DP + GCD | - |
| 14 | Minimum Cost to Connect Two Groups | Hard | [LC 1595](https://leetcode.com/problems/minimum-cost-to-connect-two-groups-of-points/) | Bitmask DP | - |
| 15 | Assignment Problem | Hard | [GFG](https://www.geeksforgeeks.org/assignment-problem-using-bitmask/) | Bitmask DP | Hungarian |

---

## 10. DIGIT DP
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Count Numbers with Unique Digits | Medium | [LC 357](https://leetcode.com/problems/count-numbers-with-unique-digits/) | Digit DP / Combinatorics | - |
| 2 | Non-negative Integers without Consecutive Ones | Hard | [LC 600](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/) | Digit DP | - |
| 3 | Numbers At Most N Given Digit Set | Hard | [LC 902](https://leetcode.com/problems/numbers-at-most-n-given-digit-set/) | Digit DP | - |
| 4 | Rotated Digits | Medium | [LC 788](https://leetcode.com/problems/rotated-digits/) | Digit DP | - |
| 5 | Count Special Integers | Hard | [LC 2376](https://leetcode.com/problems/count-special-integers/) | Digit DP | - |
| 6 | Digit Count in Range | Hard | [LC 1067](https://leetcode.com/problems/digit-count-in-range/) | Digit DP | - |
| 7 | Count Integers in Intervals | Hard | [LC 2276](https://leetcode.com/problems/count-integers-in-intervals/) | Segment tree / Digit DP | - |
| 8 | Count of Numbers from 1 to N Divisible by X | Medium | [GFG](https://www.geeksforgeeks.org/count-numbers-1-n-divisible-x/) | Digit DP | Math |
| 9 | Count Numbers with Sum of Digits = K | Medium | [GFG](https://www.geeksforgeeks.org/count-of-numbers-from-1-to-n-having-sum-of-digits-as-k/) | Digit DP | - |
| 10 | Numbers with Same First and Last Digit | Medium | [GFG](https://www.geeksforgeeks.org/count-n-digit-numbers-whose-first-last-digits-are-x-y/) | Digit DP | - |

---

## 11. DP ON GRAPHS / DAG
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Longest Path in a DAG | Medium | [GFG](https://www.geeksforgeeks.org/find-longest-path-directed-acyclic-graph/) | Topo + DP | - |
| 2 | Shortest Path in a DAG | Medium | [GFG](https://www.geeksforgeeks.org/shortest-path-for-directed-acyclic-graphs/) | Topo + DP | - |
| 3 | Count All Paths in a DAG | Medium | [GFG](https://www.geeksforgeeks.org/count-all-possible-paths-from-top-left-to-bottom-right/) | Topo + DP | - |
| 4 | Number of Ways to Arrive at Destination | Medium | [LC 1976](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/) | Dijkstra + DP | - |
| 5 | Number of Restricted Paths | Medium | [LC 1786](https://leetcode.com/problems/number-of-restricted-paths-from-first-to-last-node/) | Dijkstra + DFS/DP | - |
| 6 | Parallel Courses III | Hard | [LC 2050](https://leetcode.com/problems/parallel-courses-iii/) | Topo + DP | - |
| 7 | Minimum Cost to Reach Destination in Time | Hard | [LC 1928](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/) | DP with time state | Dijkstra |
| 8 | Longest Increasing Path in a Matrix | Hard | [LC 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | DFS + memo | Topo sort |

---

## 12. PROBABILITY & EXPECTATION DP
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Knight Probability in Chessboard | Medium | [LC 688](https://leetcode.com/problems/knight-probability-in-chessboard/) | DP probability | - |
| 2 | Out of Boundary Paths | Medium | [LC 576](https://leetcode.com/problems/out-of-boundary-paths/) | DP count paths | - |
| 3 | New 21 Game | Medium | [LC 837](https://leetcode.com/problems/new-21-game/) | Sliding window DP | - |
| 4 | Soup Servings | Medium | [LC 808](https://leetcode.com/problems/soup-servings/) | DP probability | Math |
| 5 | Probability of a Two Boxes Having Same Distinct Balls | Hard | [LC 1467](https://leetcode.com/problems/probability-of-a-two-boxes-having-the-same-number-of-distinct-balls/) | DP + combinatorics | - |
| 6 | Dice Roll Simulation | Hard | [LC 1223](https://leetcode.com/problems/dice-roll-simulation/) | DP with run-length constraint | - |
| 7 | Coin Toss Probability | Medium | [GFG](https://www.geeksforgeeks.org/coin-toss-probability-problem/) | Probability DP | - |
| 8 | Random Walk | Medium | [GFG](https://www.geeksforgeeks.org/random-walk-implementation-in-python/) | Expectation DP | - |

---

## 13. DP ON SEQUENCES (Counting / Tiling)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Count Vowels Permutation | Hard | [LC 1220](https://leetcode.com/problems/count-vowels-permutation/) | State machine DP | Matrix exp |
| 2 | Student Attendance Record II | Hard | [LC 552](https://leetcode.com/problems/student-attendance-record-ii/) | State machine DP | Matrix exp |
| 3 | Number of Music Playlists | Hard | [LC 920](https://leetcode.com/problems/number-of-music-playlists/) | 2D DP | - |
| 4 | Ways to Make a Fair Array | Medium | [LC 1664](https://leetcode.com/problems/ways-to-make-a-fair-array/) | Prefix even/odd DP | - |
| 5 | Number of Ways to Rearrange Sticks | Hard | [LC 1866](https://leetcode.com/problems/number-of-ways-to-rearrange-sticks-with-k-sticks-visible/) | Recurrence / Stirling | - |
| 6 | Tiling a Rectangle with Fewest Squares | Hard | [LC 1240](https://leetcode.com/problems/tiling-a-rectangle-with-the-fewest-squares/) | Backtracking + memo | - |
| 7 | Domino Tiling | Medium | [GFG](https://www.geeksforgeeks.org/tiling-problem/) | Fibonacci pattern | - |
| 8 | Triomin Tiling | Medium | [GFG](https://www.geeksforgeeks.org/tiling-with-dominoes/) | DP states | - |
| 9 | Number of Dice Rolls with Target Sum | Medium | [LC 1155](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/) | DP knapsack | - |
| 10 | Count Ways to Build Good Strings | Medium | [LC 2466](https://leetcode.com/problems/count-ways-to-build-good-strings/) | 1D DP | - |

---

## 14. PAINT / COLORING DP
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Paint House | Medium (Premium) | [LC 256](https://leetcode.com/problems/paint-house/) | 3-color DP | - |
| 2 | Paint House II | Hard (Premium) | [LC 265](https://leetcode.com/problems/paint-house-ii/) | k-color DP | - |
| 3 | Paint House III | Hard | [LC 1473](https://leetcode.com/problems/paint-house-iii/) | 3D DP | - |
| 4 | Paint Fence | Medium (Premium) | [LC 276](https://leetcode.com/problems/paint-fence/) | Two-state DP | - |
| 5 | Number of Ways to Color Grid | Hard | [LC 1411](https://leetcode.com/problems/number-of-ways-to-paint-n-3-grid/) | Pattern-based DP | Matrix exp |
| 6 | Flower Planting with No Adjacent | Medium | [LC 1042](https://leetcode.com/problems/flower-planting-with-no-adjacent/) | Greedy graph coloring | - |

---

## 15. ADVANCED / MISCELLANEOUS DP
### 15.1 Scheduling & Interval DP (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 1 | Maximum Profit in Job Scheduling | Hard | [LC 1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/) | Binary search + DP | Segment tree |
| 2 | Non-overlapping Intervals | Medium | [LC 435](https://leetcode.com/problems/non-overlapping-intervals/) | Greedy / DP | - |
| 3 | Video Stitching | Medium | [LC 1024](https://leetcode.com/problems/video-stitching/) | DP / Greedy | - |
| 4 | Minimum Number of Taps to Water Garden | Hard | [LC 1326](https://leetcode.com/problems/minimum-number-of-taps-to-open-to-water-a-garden/) | Jump game DP | - |
| 5 | Minimum Jumps to Reach Home | Medium | [LC 1654](https://leetcode.com/problems/minimum-jumps-to-reach-home/) | BFS / DP | - |
| 6 | Weighted Job Scheduling | Hard | [GFG](https://www.geeksforgeeks.org/weighted-job-scheduling/) | DP + binary search | - |

### 15.2 Tricky Greedy-DP Hybrids (Medium-Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 7 | Jump Game | Medium | [LC 55](https://leetcode.com/problems/jump-game/) | Greedy / DP | - |
| 8 | Jump Game II | Medium | [LC 45](https://leetcode.com/problems/jump-game-ii/) | Greedy / DP | - |
| 9 | Jump Game III | Medium | [LC 1306](https://leetcode.com/problems/jump-game-iii/) | BFS/DFS | - |
| 10 | Jump Game IV | Hard | [LC 1345](https://leetcode.com/problems/jump-game-iv/) | BFS | - |
| 11 | Minimum Number of Refueling Stops | Hard | [LC 871](https://leetcode.com/problems/minimum-number-of-refueling-stops/) | DP / Greedy + heap | - |
| 12 | Race Car | Hard | [LC 818](https://leetcode.com/problems/race-car/) | DP / BFS | - |

### 15.3 DP with Data Structures (Hard)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 13 | Count of Ranges Sum | Hard | [LC 327](https://leetcode.com/problems/count-of-range-sum/) | Merge sort / DP | Segment tree |
| 14 | Reverse Pairs | Hard | [LC 493](https://leetcode.com/problems/reverse-pairs/) | Merge sort + DP | - |
| 15 | Longest Chunked Palindrome Decomposition | Hard | [LC 1147](https://leetcode.com/problems/longest-chunked-palindrome-decomposition/) | Greedy/DP + hashing | - |
| 16 | Maximum Sum of 3 Non-Overlapping Subarrays | Hard | [LC 689](https://leetcode.com/problems/maximum-sum-of-3-non-overlapping-subarrays/) | DP with prefix | - |
| 17 | K Empty Slots | Hard (Premium) | [LC 683](https://leetcode.com/problems/k-empty-slots/) | DP / Ordered set | - |
| 18 | Data Stream as Disjoint Intervals | Hard | [LC 352](https://leetcode.com/problems/data-stream-as-disjoint-intervals/) | Sorted dict / DP | - |

### 15.4 Matrix Exponentiation (Expert)
| # | Problem Name | Difficulty | Link | Key Concept | Alternative |
|---|--------------|------------|------|-------------|-------------|
| 19 | Matrix Exponentiation (Fibonacci fast) | Expert | [GFG](https://www.geeksforgeeks.org/matrix-exponentiation/) | Matrix mult DP | - |
| 20 | Count Vowels Permutation (Fast) | Expert | [LC 1220](https://leetcode.com/problems/count-vowels-permutation/) | Matrix exp | DP |
| 21 | Student Attendance Record II (Fast) | Expert | [LC 552](https://leetcode.com/problems/student-attendance-record-ii/) | Matrix exp | DP |
| 22 | Decode Ways (Large N) | Expert | [GFG](https://www.geeksforgeeks.org/count-possible-decodings-digit-sequence/) | Matrix exp | - |

---

## 16. DP PATTERNS SUMMARY

| Pattern | Key Problems | Time Complexity |
|---------|-------------|-----------------|
| **1D Linear DP** | Fibonacci, House Robber, Coin Change | O(n) |
| **2D Grid DP** | Unique Paths, Edit Distance, LCS | O(n²) |
| **Knapsack 0/1** | Subset Sum, Partition, Target Sum | O(n·W) |
| **Unbounded Knapsack** | Coin Change, Rod Cutting | O(n·W) |
| **LIS** | LIS, Russian Doll, Box Stacking | O(n log n) |
| **Interval DP** | Burst Balloons, MCM, Stone Games | O(n³) |
| **Bitmask DP** | TSP, Assign Jobs, All Keys | O(2ⁿ · n) |
| **Digit DP** | Count integers with property | O(digits · states) |
| **Tree DP** | Tree diameter, House Robber III | O(n) |
| **State Machine DP** | Stocks, Paint, Attendance | O(n · states) |
| **Matrix Exponentiation** | Large Fibonacci, Tiling | O(k³ log n) |

---
> **Legend**: LC = LeetCode | GFG = GeeksForGeeks | Premium = requires paid subscription
