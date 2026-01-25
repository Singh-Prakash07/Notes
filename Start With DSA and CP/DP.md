[CP Handbook](https://cses.fi/book/book.pdf)
+ Read the problem.
+ Grab Pen & Paper.
+ Draw a small Recursion Tree (Inputs: n=3 or n=4).
+ Write the Recurrence Relation on paper.
+ Go to LeetCode.
+ Code Step 1 (Recursion). Run it. (Expect TLE).
+ Code Step 2 (Memoization). Submit it. (Expect Success).
+ Reflect: "Can I convert this recursion(i) to a dp[i] loop?"
+ Code Step 3 (Tabulation). Submit it.

### 🟢 Pattern 1: Linear DP (Stairs, Robbing, Tiling & Advanced)
| Category | Problem Name | Platform Link |
| :--- | :--- | :--- |
| **Stairs** | Climbing Stairs | [LeetCode 70](https://leetcode.com/problems/climbing-stairs/) |
| **Stairs** | Min Cost Climbing Stairs | [LeetCode 746](https://leetcode.com/problems/min-cost-climbing-stairs/) |
| **Frog Jump** | Geek Jump (Frog Jump) | [GFG Link](https://www.geeksforgeeks.org/problems/geek-jump/1) |
| **Frog Jump** | Frog Jump II | [LeetCode 2498](https://leetcode.com/problems/frog-jump-ii/) |
| **Robber** | House Robber | [LeetCode 198](https://leetcode.com/problems/house-robber/) |
| **Robber** | House Robber II | [LeetCode 213](https://leetcode.com/problems/house-robber-ii/) |
| **Tiling** | Domino and Tromino Tiling | [LeetCode 790](https://leetcode.com/problems/domino-and-tromino-tiling/) |
| **Tiling** | Ways to Tile a Floor | [GFG Link](https://www.geeksforgeeks.org/problems/ways-to-tile-a-floor5836/1) |
| **Decoding** | Decode Ways | [LeetCode 91](https://leetcode.com/problems/decode-ways/) |
| **Decoding** | Decode Ways II | [LeetCode 639](https://leetcode.com/problems/decode-ways-ii/) |
| **State** | Buy/Sell Stock with Transaction Fee | [LeetCode 714](https://leetcode.com/problems/714) |
| **Non-Adjacent** | Delete and Earn | [LeetCode 740](https://leetcode.com/problems/delete-and-earn/) |
| **Partition** | Integer Break | [LeetCode 343](https://leetcode.com/problems/integer-break/) |
| **Sequence** | Arithmetic Slices | [LeetCode 413](https://leetcode.com/problems/arithmetic-slices/) |
| **Jump** | Jump Game II | [LeetCode 45](https://leetcode.com/problems/jump-game-ii/) |
| **State** | Student Attendance Record II | [LeetCode 552](https://leetcode.com/problems/student-attendance-record-ii/) |
| **Grid** | Out of Boundary Paths | [LeetCode 576](https://leetcode.com/problems/out-of-boundary-paths/) |
| **Logic** | Solving Questions with Brainpower | [LeetCode 2140](https://leetcode.com/problems/solving-questions-with-brainpower/) |
| **Math** | Greatest Sum Divisible by Three | [LeetCode 1262](https://leetcode.com/problems/greatest-sum-divisible-by-three/) |
| **Split** | Restore The Array | [LeetCode 1416](https://leetcode.com/problems/restore-the-array/) |
### Pattern2: Kadane’s Algorithm & Subarray DP
*Logic: Local vs. Global decision: Start a new subarray or extend the previous one.*

| Problem Name | Variation Type / Logic | Platform Link |
| :--- | :--- | :--- |
| **Maximum Subarray** | **The Parent Problem**: Find the largest sum in a contiguous subarray. | [LeetCode 53](https://leetcode.com/problems/maximum-subarray/) |
| **Maximum Sum Circular Subarray** | Handle wrap-around subarrays using total sum minus minimum subarray. | [LeetCode 918](https://leetcode.com/problems/maximum-sum-circular-subarray/) |
| **Maximum Product Subarray** | Track both Min and Max because two negatives make a positive. | [LeetCode 152](https://leetcode.com/problems/maximum-product-subarray/) |
| **Best Time to Buy and Sell Stock** | 1 transaction: Find max difference between buy and sell price. | [LeetCode 121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) |
| **K-Concatenation Maximum Sum** | Kadane’s on a repeated array; requires prefix/suffix logic. | [LeetCode 1191](https://leetcode.com/problems/k-concatenation-maximum-sum/) |
| **Maximum Absolute Sum of Any Subarray** | Find the max of both the largest positive and largest negative subarray. | [LeetCode 1749](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/) |
| **Longest Turbulent Subarray** | Logic based on the "wiggle" (alternating sign flip) of elements. | [LeetCode 978](https://leetcode.com/problems/longest-turbulent-subarray/) |
| **Flip String to Monotone Increasing** | State transition: Decide to flip 0 to 1 or 1 to 0 at each step. | [LeetCode 926](https://leetcode.com/problems/flip-string-to-monotone-increasing/) |
| **Maximum Earnings From Taxi** | Interval-based Kadane's: Weighted subarray selection. | [LeetCode 2008](https://leetcode.com/problems/maximum-earnings-from-taxi/) |
| **House Robber** | Non-adjacent subarray sum: Extend from i-2 or skip. | [LeetCode 198](https://leetcode.com/problems/house-robber/) |
| **Maximum Subarray Sum with One Deletion** | Maintain two states: "not deleted" and "already deleted one." | [LeetCode 1186](https://leetcode.com/problems/maximum-subarray-sum-with-one-deletion/) |
| **Smallest Subarray with Sum > X** | The "Minimum" version of Kadane's using sliding window logic. | [GFG Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1) |
| **Maximum Sum of 3 Non-Overlapping Subarrays** | Combining window sums with DP to pick three distinct segments. | [LeetCode 689](https://leetcode.com/problems/maximum-sum-of-3-non-overlapping-subarrays/) |
| **Maximum Sum Rectangle in a 2D Matrix** | Reduces 2D matrix into 1D columns and applies Kadane’s logic. | [GFG Link](https://www.geeksforgeeks.org/problems/maximum-sum-rectangle0832/1) |
| **Maximum Score from Performing Multiplications** | Subarray "ends" logic: picking from the front or back of the array. | [LeetCode 1770](https://leetcode.com/problems/maximum-score-from-performing-multiplication-operations/) |
| **Maximum Score of a Spliced Array** | Find "Max Gain" using Kadane’s on the difference between arrays. | [LeetCode 2321](https://leetcode.com/problems/maximum-score-of-a-spliced-array/) |
| **Max Sum of Rectangle No Larger Than K** | 2D Kadane's with a specific sum constraint using TreeSet/Binary Search. | [LeetCode 363](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/) |
| **Best Time to Buy and Sell Stock with Cooldown** | State-machine DP logic applied to a subarray decision. | [LeetCode 309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) |
| **Maximum Subarray Sum with at most K elements** | Kadane's logic combined with a Deque or Sliding Window constraint. | [GFG Link](https://www.geeksforgeeks.org/problems/maximum-sum-of-subarray-of-size-at-most-k/1) |
| **Maximum Sum of Subarray of size K** | Fixed window Kadane's: Sliding window basics for subarray sums. | [GFG Link](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1) |
### Pattern 3: 0/1 Knapsack (The Father of DP)
+ **Core Concept**: You have items with Weight & Value. Max capacity W. You can either Pick or Don't Pick.

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Standard | 0-1 Knapsack Problem | [GFG](https://www.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1) |
| Standard | Knapsack with Duplicate Items | [GFG](https://www.geeksforgeeks.org/problems/knapsack-with-duplicate-items4201/1) |
| Subset Sum | Subset Sum Problem | [GFG](https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1) |
| Subset Sum | Partition Equal Subset Sum | [LeetCode 416](https://leetcode.com/problems/partition-equal-subset-sum/) |
| Equal Partition | Partition Equal Subset Sum | [LeetCode 416](https://leetcode.com/problems/partition-equal-subset-sum/) |
| Equal Partition | Partition to K Equal Sum Subsets | [LeetCode 698](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/) |
| Count Subsets | Perfect Sum Problem | [GFG](https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1) |
| Count Subsets | Combination Sum IV | [LeetCode 377](https://leetcode.com/problems/combination-sum-iv/) |
| Min Sum Diff | Minimum Sum Partition | [GFG](https://www.geeksforgeeks.org/problems/minimum-sum-partition3317/1) |
| Min Sum Diff | Last Stone Weight II | [LeetCode 1049](https://leetcode.com/problems/last-stone-weight-ii/) |
| Target Sum | Target Sum | [LeetCode 494](https://leetcode.com/problems/target-sum/) |
| Target Sum | Expression Add Operators | [LeetCode 282](https://leetcode.com/problems/expression-add-operators/) |
| **Target Sum** | Assign signs to reach target. | [LeetCode 494](https://leetcode.com/problems/target-sum/) |
| **Last Stone Weight II** | Minimize difference between two subset sums. | [LeetCode 1049](https://leetcode.com/problems/last-stone-weight-ii/) |
| **Ones and Zeroes** | Knapsack with two independent capacities. | [LeetCode 474](https://leetcode.com/problems/ones-and-zeroes/) |
| **Tallest Billboard** | Track difference of two subset sums. | [LeetCode 956](https://leetcode.com/problems/tallest-billboard/) |
| **Profitable Schemes** | Knapsack with a "minimum profit" gate. | [LeetCode 879](https://leetcode.com/problems/profitable-schemes/) |
| **Partition Into 2 Arrays** | Minimize sum difference (Meet-in-the-middle). | [LeetCode 2035](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/) |

### Pattern 4: Unbounded Knapsack
+ **Core Concept**: Same as 0/1, but you can pick the same item multiple times.

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Standard | Unbounded Knapsack | [GFG](https://www.geeksforgeeks.org/problems/knapsack-with-duplicate-items4201/1) |
| Standard | Form Largest Integer with Target | [LeetCode 1449](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/) |
| Rod Cutting | Rod Cutting | [GFG](https://www.geeksforgeeks.org/problems/rod-cutting0840/1) |
| Rod Cutting | Integer Break | [LeetCode 343](https://leetcode.com/problems/integer-break/) |
| Coin Change I | Coin Change II (Max Ways) | [LeetCode 518](https://leetcode.com/problems/coin-change-2/) |
| Coin Change I | Ways to Make a Fair Array | [LeetCode 1664](https://leetcode.com/problems/ways-to-make-a-fair-array/) |
| Coin Change II | Coin Change (Min Coins) | [LeetCode 322](https://leetcode.com/problems/coin-change/) |
| Coin Change II | Min Cost For Tickets | [LeetCode 983](https://leetcode.com/problems/minimum-cost-for-tickets/) |
| Ribbon Cut | Maximize The Cut Segments | [GFG](https://www.geeksforgeeks.org/problems/cutted-segments1642/1) |
| Ribbon Cut | Perfect Squares | [LeetCode 279](https://leetcode.com/problems/perfect-squares/) |

### Pattern 5: Longest Common Subsequence (LCS)
+ **Core Concept**: Matching two strings/sequences.
+ State: dp[i][j] = matching length of s1[0..i] and s2[0..j].

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Standard | Longest Common Subsequence | [LeetCode 1143](https://leetcode.com/problems/longest-common-subsequence/) |
| Standard | Uncrossed Lines | [LeetCode 1035](https://leetcode.com/problems/uncrossed-lines/) |
| Substring | Longest Common Substring | [GFG](https://www.geeksforgeeks.org/problems/longest-common-substring1452/1) |
| Substring | Max Length of Repeated Subarray | [LeetCode 718](https://leetcode.com/problems/maximum-length-of-repeated-subarray/) |
| Print LCS | Print All LCS Sequences | [GFG](https://www.geeksforgeeks.org/problems/print-all-lcs-sequences-1587115621/1) |
| Print LCS | Shortest Common Supersequence | [LeetCode 1092](https://leetcode.com/problems/shortest-common-supersequence/) |
| SCS | Shortest Common Supersequence | [LeetCode 1092](https://leetcode.com/problems/shortest-common-supersequence/) |
| SCS | Shortest Common Supersequence (Length) | [GFG](https://www.geeksforgeeks.org/problems/shortest-common-supersequence0322/1) |
| Edit A to B | Delete Operation for Two Strings | [LeetCode 583](https://leetcode.com/problems/delete-operation-for-two-strings/) |
| Edit A to B | Minimum ASCII Delete Sum | [LeetCode 712](https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings/) |
| Palindrome | Longest Palindromic Subsequence | [LeetCode 516](https://leetcode.com/problems/longest-palindromic-subsequence/) |
| Palindrome | Max Product of Two Palindromic Subseq | [LeetCode 2002](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/) |
| Min Del/Pal | Min Insertions to Make Palindrome | [LeetCode 1312](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/) |
| Min Del/Pal | Valid Palindrome III | [LeetCode 1216](https://leetcode.com/problems/valid-palindrome-iii/) |
| Repeating | Longest Repeating Subsequence | [GFG](https://www.geeksforgeeks.org/problems/longest-repeating-subsequence2004/1) |
| Repeating | Longest Substring Without Repeating | [LeetCode 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/) |
| Pattern Match | Is Subsequence | [LeetCode 392](https://leetcode.com/problems/is-subsequence/) |
| Pattern Match | Number of Matching Subsequences | [LeetCode 792](https://leetcode.com/problems/number-of-matching-subsequences/) |
| Bitonic | Longest Bitonic Subsequence | [GFG](https://www.geeksforgeeks.org/problems/longest-bitonic-subsequence0824/1) |
| Bitonic | Min Removals to Make Mountain Array | [LeetCode 1671](https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/) |
| Wiggle | Wiggle Subsequence | [LeetCode 376](https://leetcode.com/problems/wiggle-subsequence/) |
| Wiggle | Longest Alternating Subsequence | [GFG](https://www.geeksforgeeks.org/problems/longest-alternating-subsequence5951/1) |
| Distinct | Distinct Subsequences | [LeetCode 115](https://leetcode.com/problems/distinct-subsequences/) |
| Distinct | Distinct Subsequences II | [LeetCode 940](https://leetcode.com/problems/distinct-subsequences-ii/) |
| Interleaving | Interleaving String | [LeetCode 97](https://leetcode.com/problems/interleaving-string/) |
| Interleaving | Scramble String | [LeetCode 87](https://leetcode.com/problems/scramble-string/) |


### Pattern 6: DP on Grids
+ **Core Concept**: dp[i][j] depends on dp[i-1][j] (Top) and dp[i][j-1] (Left).

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Standard | Longest Increasing Subsequence | [LeetCode 300](https://leetcode.com/problems/longest-increasing-subsequence/) |
| Standard | Number of Longest Increasing Subseq | [LeetCode 673](https://leetcode.com/problems/number-of-longest-increasing-subsequence/) |
| Envelopes | Russian Doll Envelopes | [LeetCode 354](https://leetcode.com/problems/russian-doll-envelopes/) |
| Envelopes | Max Height by Stacking Cuboids | [LeetCode 1691](https://leetcode.com/problems/maximum-height-by-stacking-cuboids/) |
| Max Sum | Maximum Sum Increasing Subsequence | [GFG](https://www.geeksforgeeks.org/problems/maximum-sum-increasing-subsequence4749/1) |
| Max Sum | Best Team With No Conflicts | [LeetCode 1626](https://leetcode.com/problems/best-team-with-no-conflicts/) |
| String Chain | Longest String Chain | [LeetCode 1048](https://leetcode.com/problems/longest-string-chain/) |
| String Chain | Largest Divisible Subset | [LeetCode 368](https://leetcode.com/problems/largest-divisible-subset/) |
| Min Removals | Shortest Subarray to be Removed | [LeetCode 1574](https://leetcode.com/problems/shortest-subarray-to-be-removed-to-make-array-sorted/) |
| Min Removals | Min Deletions to Make Sorted Array | [GFG](https://www.geeksforgeeks.org/problems/minimum-deletions-to-make-sorted-array/1) |

### Pattern 7: Longest Increasing Subsequence (LIS)
+ **Core Concept**: dp[i] = max length ending at index i.

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Unique Paths | Unique Paths | [LeetCode 62](https://leetcode.com/problems/unique-paths/) |
| Unique Paths | Unique Paths II | [LeetCode 63](https://leetcode.com/problems/unique-paths-ii/) |
| Min Path Sum | Minimum Path Sum | [LeetCode 64](https://leetcode.com/problems/minimum-path-sum/) |
| Min Path Sum | Minimum Falling Path Sum | [LeetCode 931](https://leetcode.com/problems/minimum-falling-path-sum/) |
| Cherry Pickup | Cherry Pickup | [LeetCode 741](https://leetcode.com/problems/cherry-pickup/) |
| Cherry Pickup | Cherry Pickup II | [LeetCode 1463](https://leetcode.com/problems/cherry-pickup-ii/) |
| Squares | Maximal Square | [LeetCode 221](https://leetcode.com/problems/maximal-square/) |
| Squares | Maximal Rectangle | [LeetCode 85](https://leetcode.com/problems/maximal-rectangle/) |
| Dungeon | Dungeon Game | [LeetCode 174](https://leetcode.com/problems/dungeon-game/) |
| Dungeon | Minimum Path Cost in a Grid | [LeetCode 2304](https://leetcode.com/problems/minimum-path-cost-in-a-grid/) |


### Pattern 8: Matrix Chain Multiplication (MCM)
+ **Core Concept**: Find the optimal place to "cut" (k) in a range (i to j).
+ Loop: for(k = i; k < j; k++)

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Standard | Matrix Chain Multiplication | [GFG](https://www.geeksforgeeks.org/problems/matrix-chain-multiplication0303/1) |
| Standard | Burst Balloons | [LeetCode 312](https://leetcode.com/problems/burst-balloons/) |
| Pal Partition | Palindrome Partitioning II | [LeetCode 132](https://leetcode.com/problems/palindrome-partitioning-ii/) |
| Pal Partition | Palindrome Partitioning IV | [LeetCode 1745](https://leetcode.com/problems/palindrome-partitioning-iv/) |
| Boolean | Boolean Parenthesization | [GFG](https://www.geeksforgeeks.org/problems/boolean-parenthesization5610/1) |
| Boolean | Parsing A Boolean Expression | [LeetCode 1106](https://leetcode.com/problems/parsing-a-boolean-expression/) |
| Scramble | Scramble String | [LeetCode 87](https://leetcode.com/problems/scramble-string/) |
| Scramble | Swap for Longest Repeated Substring | [LeetCode 1156](https://leetcode.com/problems/swap-for-longest-repeated-character-substring/) |
| Egg Drop | Super Egg Drop | [LeetCode 887](https://leetcode.com/problems/super-egg-drop/) |
| Egg Drop | Egg Dropping Puzzle | [GFG](https://www.geeksforgeeks.org/problems/egg-dropping-puzzle-1587115620/1) |

### Pattern 9: DP on Stocks (State Machine)
+ **Core Concept**: dp[day][holding_status][transaction_count]

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Max Subarray | Maximum Subarray | [LeetCode 53](https://leetcode.com/problems/maximum-subarray/) |
| Max Subarray | Max Absolute Sum of Any Subarray | [LeetCode 1749](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/) |
| Max Product | Maximum Product Subarray | [LeetCode 152](https://leetcode.com/problems/maximum-product-subarray/) |
| Max Product | Subarray Product Less Than K | [LeetCode 713](https://leetcode.com/problems/subarray-product-less-than-k/) |
| Circular | Maximum Sum Circular Subarray | [LeetCode 918](https://leetcode.com/problems/maximum-sum-circular-subarray/) |
| Circular | Max Length of Subarray Pos Product | [LeetCode 1567](https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/) |
| 2D Matrix | Maximum Sum Rectangle | [GFG](https://www.geeksforgeeks.org/problems/maximum-sum-rectangle-29/1) |
| 2D Matrix | Max Sum of Rectangle No Larger Than K | [LeetCode 363](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/) |

### Pattern 10: DP on Trees
+ **Core Concept**: Use recursion to return values from Left and Right children to answer the parent.

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| Diameter | Diameter of Binary Tree | [LeetCode 543](https://leetcode.com/problems/diameter-of-binary-tree/) |
| Diameter | Diameter of N-Ary Tree | [LeetCode 1522](https://leetcode.com/problems/diameter-of-n-ary-tree/) |
| Path Any-Any | Binary Tree Maximum Path Sum | [LeetCode 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/) |
| Path Any-Any | Max Path Sum from Any Node | [GFG](https://www.geeksforgeeks.org/problems/maximum-path-sum-from-any-node/1) |
| Path Leaf-Leaf | Max Path Sum Leaf to Leaf | [GFG](https://www.geeksforgeeks.org/problems/maximum-path-sum/1) |
| Path Leaf-Leaf | Path Sum II | [LeetCode 113](https://leetcode.com/problems/path-sum-ii/) |
| Robber | House Robber III | [LeetCode 337](https://leetcode.com/problems/house-robber-iii/) |
| Robber | Longest Univalue Path | [LeetCode 687](https://leetcode.com/problems/longest-univalue-path/) |
| LCA | Lowest Common Ancestor of Binary Tree | [LeetCode 236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) |
| LCA | Kth Ancestor of a Tree Node | [LeetCode 1483](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) |

### Pattern 11: Partition/Gap Strategy
+ **Core Concept**: Similar to MCM but often involves game theory or palindromes.

| **Variation** | **Problem Name** | **Platform Link** |
| :--- | :--- | :--- |
| 1 Trans | Best Time to Buy and Sell Stock | [LeetCode 121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) |
| 1 Trans | Max Difference Between Incr Elements | [LeetCode 2016](https://leetcode.com/problems/maximum-difference-between-increasing-elements/) |
| Unlimited | Best Time to Buy and Sell Stock II | [LeetCode 122](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) |
| Unlimited | Best Time to Buy and Sell with Fee | [LeetCode 714](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/) |
| 2 Trans | Best Time to Buy and Sell Stock III | [LeetCode 123](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) |
| 2 Trans | Best Time to Buy and Sell Stock IV | [LeetCode 188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) |
| Cooldown | Best Time to Buy and Sell with Cooldown | [LeetCode 309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) |
| Cooldown | Minimum Number of Days to Bloom | [LeetCode 1482](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/) |
| k Trans | Best Time to Buy and Sell Stock IV | [LeetCode 188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) |
| k Trans | Maximum Profit From Trading Stocks | [LeetCode 2291](https://leetcode.com/problems/maximum-profit-from-trading-stocks/) |
+ Digit DP & Bitmask DP
