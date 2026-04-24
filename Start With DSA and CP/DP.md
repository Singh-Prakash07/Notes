# DYNAMIC PROGRAMMING
---

## 1. 1D LINEAR DP

### 1.1 Fibonacci Recurrence — Direct State
> **Core idea:** `dp[i]` depends only on `dp[i-1]` and `dp[i-2]` (or `dp[i-3]`). Fixed small window. Space optimizable to O(1).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Fibonacci Number | Easy | [LC 509](https://leetcode.com/problems/fibonacci-number/) | dp[i] = dp[i-1] + dp[i-2] | Math formula |
| 2 | Climbing Stairs | Easy | [LC 70](https://leetcode.com/problems/climbing-stairs/) | Same recurrence as Fibonacci | Matrix exp |
| 3 | Min Cost Climbing Stairs | Easy | [LC 746](https://leetcode.com/problems/min-cost-climbing-stairs/) | dp[i] = min(dp[i-1], dp[i-2]) + cost[i] | - |
| 4 | N-th Tribonacci Number | Easy | [LC 1137](https://leetcode.com/problems/n-th-tribonacci-number/) | dp[i] = dp[i-1]+dp[i-2]+dp[i-3] | - |
| 5 | Count Ways to Reach nth Stair | Easy | [GFG](https://www.geeksforgeeks.org/count-ways-reach-nth-stair/) | Generalized steps variant | - |
| 6 | Frog Jump (1 or 2 steps) | Easy | [GFG](https://www.geeksforgeeks.org/count-number-of-ways-to-cover-a-distance/) | dp[i] = dp[i-1] + dp[i-2] | - |

### 1.2 Fibonacci Recurrence — With Tiling State Transitions
> **Core idea:** States encode partially-filled configurations (e.g., a 2×i board half-filled with a domino). The recurrence tracks how many ways to complete from each configuration.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 7 | Domino and Tromino Tiling | Medium | [LC 790](https://leetcode.com/problems/domino-and-tromino-tiling/) | 3-state DP: full, top-half, bottom-half | - |
| 8 | Domino Tiling (2×n) | Medium | [GFG](https://www.geeksforgeeks.org/tiling-problem/) | Classic dp[i] = dp[i-1] + dp[i-2] | - |
| 9 | Triomin / L-Tromino Tiling | Medium | [GFG](https://www.geeksforgeeks.org/tiling-with-dominoes/) | dp states for partial configurations | - |
| 10 | Number of Ways to Paint N×3 Grid | Hard | [LC 1411](https://leetcode.com/problems/number-of-ways-to-paint-n-3-grid/) | Count valid row patterns → multiply | Matrix exp |

### 1.3 Non-Adjacent Selection (House Robber Pattern)
> **Core idea:** At each index you choose to take or skip. Taking index `i` means `i-1` is forbidden. `dp[i] = max(dp[i-2] + val[i], dp[i-1])`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | House Robber | Medium | [LC 198](https://leetcode.com/problems/house-robber/) | dp[i] = max(dp[i-1], dp[i-2]+nums[i]) | - |
| 12 | Delete and Earn | Medium | [LC 740](https://leetcode.com/problems/delete-and-earn/) | Transform: bucket by value → House Robber | - |
| 13 | Wiggle Subsequence | Medium | [LC 376](https://leetcode.com/problems/wiggle-subsequence/) | up/down 2-state DP, greedy peaks | Greedy |
| 14 | Maximum Alternating Subsequence Sum | Medium | [LC 1911](https://leetcode.com/problems/maximum-alternating-subsequence-sum/) | 2-state: even-indexed max, odd-indexed | - |
| 15 🆕 | Count Number of Ways to Place Houses | Medium | [LC 2320](https://leetcode.com/problems/count-number-of-ways-to-place-houses/) | Two-side House Robber, multiply results | - |

### 1.4 Circular Array — Two-Pass Trick
> **Core idea:** Break circle into two separate runs: [0..n-2] and [1..n-1], take max of both.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 16 | House Robber II | Medium | [LC 213](https://leetcode.com/problems/house-robber-ii/) | Run House Robber twice, exclude last / first | - |
| 17 | Maximum Sum Circular Subarray | Medium | [LC 918](https://leetcode.com/problems/maximum-sum-circular-subarray/) | max(kadane, total - min_subarray) | - |

### 1.5 Kadane's Algorithm — Maximum Subarray Variants
> **Core idea:** `dp[i]` = best subarray **ending at index i**. `dp[i] = max(nums[i], dp[i-1] + nums[i])`. Global answer = max over all dp[i].

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Maximum Subarray | Medium | [LC 53](https://leetcode.com/problems/maximum-subarray/) | Classic Kadane | Divide & Conquer |
| 19 | Maximum Product Subarray | Medium | [LC 152](https://leetcode.com/problems/maximum-product-subarray/) | Track both min and max (negatives flip) | - |
| 20 | Longest Turbulent Subarray | Medium | [LC 978](https://leetcode.com/problems/longest-turbulent-subarray/) | 2-state Kadane: inc[i], dec[i] | Sliding window |
| 21 | Maximum Subarray Sum with One Deletion | Medium | [LC 1186](https://leetcode.com/problems/maximum-subarray-sum-with-one-deletion/) | 2-state: with deletion used, without | - |
| 22 | K-Concatenation Maximum Sum | Medium | [LC 1191](https://leetcode.com/problems/k-concatenation-maximum-sum/) | Kadane + total sum formula for k≥2 | - |
| 23 🆕 | Best Sightseeing Pair | Medium | [LC 1014](https://leetcode.com/problems/best-sightseeing-pair/) | max(A[i]+i) + A[j]-j; track running max of A[i]+i | - |

### 1.6 Arithmetic / Pattern Subsequence DP (HashMap-Augmented)
> **Core idea:** Use a HashMap keyed by the pattern property (common difference, etc.). `dp[i][diff] = dp[j][diff] + 1`. HashMap makes lookup O(1).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 24 | Arithmetic Slices | Medium | [LC 413](https://leetcode.com/problems/arithmetic-slices/) | dp[i] = dp[i-1]+1 if diff matches | - |
| 25 | Arithmetic Slices II — Subsequence | Hard | [LC 446](https://leetcode.com/problems/arithmetic-slices-ii-subsequence/) | dp[i][diff] = sum of dp[j][diff]+1 | - |
| 26 | Longest Arithmetic Subsequence | Medium | [LC 1027](https://leetcode.com/problems/longest-arithmetic-subsequence/) | dp[i][diff] = dp[j][diff]+1 | - |
| 27 | Longest Arithmetic Subsequence of Given Difference | Medium | [LC 1218](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/) | HashMap: dp[num] = dp[num-diff]+1 | - |
| 28 | Number of Arithmetic Triplets | Easy | [LC 2367](https://leetcode.com/problems/number-of-arithmetic-triplets/) | HashMap count pairs | - |

### 1.7 String Partition / Decode DP
> **Core idea:** `dp[i]` = ways/feasibility to decode prefix of length i. Look back 1 or 2+ characters.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 29 | Decode Ways | Medium | [LC 91](https://leetcode.com/problems/decode-ways/) | dp[i] depends on 1-char and 2-char lookback | - |
| 30 | Decode Ways II (with *) | Hard | [LC 639](https://leetcode.com/problems/decode-ways-ii/) | Multiply by wildcard choices | - |
| 31 | Word Break | Medium | [LC 139](https://leetcode.com/problems/word-break/) | dp[i] = OR over all valid word endings at i | BFS, Trie |
| 32 | Word Break II (All Partitions) | Hard | [LC 140](https://leetcode.com/problems/word-break-ii/) | Backtracking + memoization | - |
| 33 | Restore IP Addresses | Medium | [LC 93](https://leetcode.com/problems/restore-ip-addresses/) | Backtracking / DP with segment constraints | - |
| 34 🆕 | Extra Characters in a String | Medium | [LC 2707](https://leetcode.com/problems/extra-characters-in-a-string/) | dp[i] = min extras; check all words ending at i | Trie |

### 1.8 Cost Minimization on Fixed-Structure (DP on Days/Tickets)
> **Core idea:** `dp[i]` = min cost to cover all travel up to day i. Either skip or buy a pass.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 35 | Minimum Cost For Tickets | Medium | [LC 983](https://leetcode.com/problems/minimum-cost-for-tickets/) | dp[i] = min of 1/7/30-day pass lookback | - |
| 36 | Perfect Squares | Medium | [LC 279](https://leetcode.com/problems/perfect-squares/) | dp[i] = 1 + min(dp[i - sq]) | BFS, Math |
| 37 | Minimum Jumps | Medium | [GFG](https://www.geeksforgeeks.org/minimum-number-of-jumps-to-reach-end-of-a-given-array/) | dp[i] = min jumps to reach i | Greedy |

### 🆕 1.9 Decision DP — Take Now or Skip with Variable Jump
> **Core idea:** At position i, taking it gives reward but forces skip to position `i + skip[i]`. Skipping moves to `i + 1`. Often solved right-to-left: `dp[i] = max(reward[i] + dp[i+skip[i]], dp[i+1])`. The "future cost of taking" is embedded in the problem.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Solving Questions with Brainpower | Medium | [LC 2140](https://leetcode.com/problems/solving-questions-with-brainpower/) | dp[i] = max(pts+dp[i+skip], dp[i+1]); right-to-left | - |
| 2 | Maximum Jumps to Reach Last Index | Hard | [LC 2770](https://leetcode.com/problems/maximum-number-of-jumps-to-reach-the-last-index/) | dp[i] = max jumps to reach i within target diff | - |
| 3 | Greatest Sum Divisible by Three | Medium | [LC 1262](https://leetcode.com/problems/greatest-sum-divisible-by-three/) | 3-state modular DP: dp[rem] = max sum with given remainder | - |
| 4 | Number of Ways to Reach a Position | Medium | [LC 2400](https://leetcode.com/problems/number-of-ways-to-reach-a-position-after-exactly-k-steps/) | Count exact-step paths with parity | - |

---

## 2. KNAPSACK DP

### 2.1 0/1 Knapsack — Boolean Feasibility (Can We Reach?)
> **Core idea:** `dp[j]` = true if sum j is achievable. Iterate j **backward** to ensure each item used at most once.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | 0/1 Knapsack Problem | Medium | [GFG](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/) | dp[w] = max value using capacity w | - |
| 2 | Subset Sum Problem | Medium | [GFG](https://www.geeksforgeeks.org/subset-sum-problem-dp-25/) | dp[s] = can we form sum s? | - |
| 3 | Partition Equal Subset Sum | Medium | [LC 416](https://leetcode.com/problems/partition-equal-subset-sum/) | Can we form sum = total/2? | - |
| 4 | Check if There is a Valid Partition | Medium | [LC 2369](https://leetcode.com/problems/check-if-there-is-a-valid-partition-for-the-array/) | dp[i] = can array[0..i] be validly partitioned? | - |
| 5 🆕 | Number of Great Partitions | Hard | [LC 2518](https://leetcode.com/problems/number-of-great-partitions/) | Count partitions via complement: total - bad (knapsack count) | - |

### 2.2 0/1 Knapsack — Counting Variants (How Many Ways?)
> **Core idea:** `dp[j]` = number of subsets that form sum j. Transition: `dp[j] += dp[j - nums[i]]`. Backward iteration.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Count Subsets with Given Sum | Medium | [GFG](https://www.geeksforgeeks.org/count-of-subsets-with-sum-equal-to-x/) | dp[s] = count of subsets summing to s | - |
| 7 | Target Sum | Medium | [LC 494](https://leetcode.com/problems/target-sum/) | Count subsets; +/- → two groups formula | DFS+memo |
| 8 | Count Subsets with Given Difference | Medium | [GFG](https://www.geeksforgeeks.org/number-of-subsets-with-given-difference/) | s1-s2=diff, s1+s2=total → find s1 | - |

### 2.3 0/1 Knapsack — Optimization (Min Diff / Max Value)
> **Core idea:** Fill boolean knapsack, scan from total/2 downward for largest reachable sum. Min diff = total - 2*(largest reachable ≤ total/2).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Minimum Subset Sum Difference | Medium | [GFG](https://www.geeksforgeeks.org/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum/) | Fill knapsack, find max s ≤ total/2 | - |
| 10 | Last Stone Weight II | Medium | [LC 1049](https://leetcode.com/problems/last-stone-weight-ii/) | Same: min diff = min(|S1-S2|) | - |
| 11 | Partition Array Into Two Arrays with Min Sum Diff | Hard | [LC 2035](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/) | Meet in the middle + binary search | Section 19 |

### 2.4 0/1 Knapsack — 2D (Two Constraints)
> **Core idea:** Two independent capacity constraints. DP table becomes 2D. Iterate backward on both dimensions.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Ones and Zeroes | Medium | [LC 474](https://leetcode.com/problems/ones-and-zeroes/) | dp[m][n] = max strings with m zeros, n ones | - |
| 13 | Profitable Schemes | Hard | [LC 879](https://leetcode.com/problems/profitable-schemes/) | dp[members][profit] = count of schemes | - |
| 14 | Shopping Offers | Medium | [LC 638](https://leetcode.com/problems/shopping-offers/) | State = remaining items needed, DFS+memo | - |
| 15 🆕 | Tallest Billboard | Hard | [LC 956](https://leetcode.com/problems/tallest-billboard/) | dp[diff] = max min-side when rod difference is diff | - |
| 16 🆕 | Toss Strange Coins | Medium | [LC 1230](https://leetcode.com/problems/toss-strange-coins/) | dp[j] = prob of exactly j heads; probability knapsack | - |

### 2.5 Unbounded Knapsack — Minimum Count
> **Core idea:** Each item usable unlimited times. Iterate j **forward**. `dp[j] = min(dp[j], dp[j - coin] + 1)`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 17 | Coin Change (Min Coins) | Medium | [LC 322](https://leetcode.com/problems/coin-change/) | dp[i] = 1 + min(dp[i-coin]) | BFS |
| 18 | Perfect Squares | Medium | [LC 279](https://leetcode.com/problems/perfect-squares/) | Coins = perfect squares | BFS, Math |
| 19 | Minimum Ribbon Cut | Medium | [GFG](https://www.geeksforgeeks.org/minimum-cuts-ribbon/) | Min pieces to cut ribbon | - |
| 20 | Minimum Cost to Fill a Bag | Medium | [GFG](https://www.geeksforgeeks.org/minimum-cost-to-fill-given-weight-in-a-bag/) | Unbounded with per-unit costs | - |

### 2.6 Unbounded Knapsack — Count Ways
> **Core idea:** `dp[j] += dp[j - coin]` forward. Outer=items, inner=targets → combinations. Swapped = permutations.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 21 | Coin Change II (Count Ways) | Medium | [LC 518](https://leetcode.com/problems/coin-change-ii/) | Items outer, target inner → combinations | - |
| 22 | Combination Sum IV (Count Permutations) | Medium | [LC 377](https://leetcode.com/problems/combination-sum-iv/) | Target outer, items inner → ordered perms | - |
| 23 | Count Ways to Build Good Strings | Medium | [LC 2466](https://leetcode.com/problems/count-ways-to-build-good-strings/) | dp[i] += dp[i-zero] + dp[i-one] | - |
| 24 | Number of Dice Rolls with Target Sum | Medium | [LC 1155](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/) | Bounded: k dice each 1..f | - |

### 2.7 Unbounded Knapsack — Maximum Value
> **Core idea:** `dp[j] = max(dp[j], dp[j - len] + price[len])` forward. Maximize value with repeating items.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Unbounded Knapsack | Medium | [GFG](https://www.geeksforgeeks.org/unbounded-knapsack-repetition-items-allowed/) | Classic max-value unbounded | - |
| 26 | Rod Cutting | Medium | [GFG](https://www.geeksforgeeks.org/cutting-a-rod-dp-13/) | dp[i] = max(price[j] + dp[i-j]) | - |
| 27 | Integer Break | Medium | [LC 343](https://leetcode.com/problems/integer-break/) | dp[i] = max(j*(i-j), j*dp[i-j]) | Math |
| 28 | Maximum Ribbon Cut | Medium | [GFG](https://www.geeksforgeeks.org/maximum-number-of-pieces-of-given-lengths/) | Max pieces, unbounded | - |

### 2.8 Multi-Dimensional Knapsack — Job/Task Scheduling
> **Core idea:** Sort by end time. `dp[i]` = max profit. Binary search for latest non-conflicting job j.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 29 | Maximum Profit in Job Scheduling | Hard | [LC 1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/) | Sort by end + binary search dp | Segment tree |
| 30 | Minimum Difficulty of a Job Schedule | Hard | [LC 1335](https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/) | dp[d][i] = min difficulty for d days, first i jobs | - |
| 31 | Weighted Job Scheduling | Hard | [GFG](https://www.geeksforgeeks.org/weighted-job-scheduling/) | Sort + binary search DP | - |

### 2.9 Knapsack — K Inverse Pairs / Order-Constrained
> **Core idea:** `dp[n][k]` = count of permutations of 1..n with exactly k inverse pairs. Transition uses prefix sums to avoid O(n³).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 32 | K Inverse Pairs Array | Hard | [LC 629](https://leetcode.com/problems/k-inverse-pairs-array/) | dp[n][k] = dp[n-1][k] - dp[n-1][k-n] + prefix | - |

---

## 3. STRING DP

### 3.1 LCS — Classic and Reconstruction
> **Core idea:** `dp[i][j]` = LCS length of s1[0..i-1] and s2[0..j-1]. Match → `dp[i-1][j-1]+1`. Else → `max(dp[i-1][j], dp[i][j-1])`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Longest Common Subsequence | Medium | [LC 1143](https://leetcode.com/problems/longest-common-subsequence/) | Classic 2D LCS | - |
| 2 | Print LCS | Medium | [GFG](https://www.geeksforgeeks.org/printing-longest-common-subsequence/) | Reconstruct from dp table | - |
| 3 | Uncrossed Lines | Medium | [LC 1035](https://leetcode.com/problems/uncrossed-lines/) | LCS disguised as line-crossing | - |
| 4 | Longest Repeating Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/longest-repeating-subsequence/) | LCS(s, s) with constraint i≠j | - |
| 5 | Sequence Pattern Matching | Easy | [GFG](https://www.geeksforgeeks.org/given-two-strings-find-first-string-subsequence-second/) | LCS(s1, s2) == len(s1) | - |

### 3.2 LCS — Deletion / Insertion Cost Variants
> **Core idea:** Transform LCS into "minimum operations." Deletions to make equal = (len1-LCS)+(len2-LCS). Weighted: minimize ASCII sum deleted.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Delete Operations for Two Strings | Medium | [LC 583](https://leetcode.com/problems/delete-operation-for-two-strings/) | (n - LCS) + (m - LCS) | - |
| 7 | Minimum ASCII Delete Sum for Two Strings | Medium | [LC 712](https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings/) | Weighted LCS (maximize sum kept) | - |
| 8 | Shortest Common Supersequence | Hard | [LC 1092](https://leetcode.com/problems/shortest-common-supersequence/) | n + m - LCS, then reconstruct | - |
| 9 | Minimum Insertions to Make String Palindrome | Hard | [LC 1312](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/) | n - LCS(s, reverse(s)) | - |
| 10 | Longest Palindromic Subsequence | Medium | [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/) | LCS(s, reverse(s)) | Interval DP |

### 3.3 LCS — Contiguous Variant (Substring)
> **Core idea:** `dp[i][j]` = length of **common substring** ending at s1[i-1] and s2[j-1]. `dp[i][j] = dp[i-1][j-1]+1` if match, else 0.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Longest Common Substring | Medium | [GFG](https://www.geeksforgeeks.org/longest-common-substring-dp-29/) | dp[i][j]=dp[i-1][j-1]+1 if match, else 0 | Binary search+hash |
| 12 | Maximum Length of Repeated Subarray | Medium | [LC 718](https://leetcode.com/problems/maximum-length-of-repeated-subarray/) | Same as LCS contiguous on arrays | Binary search+hash |
| 13 🆕 | Longest Repeating Substring | Medium (Premium) | [LC 1062](https://leetcode.com/problems/longest-repeating-substring/) | LCS(s,s) contiguous with i≠j constraint | Suffix array |

### 3.4 LIS — O(n²) DP
> **Core idea:** `dp[i]` = length of LIS ending at index i. For each j<i where nums[j]<nums[i]: `dp[i]=max(dp[i],dp[j]+1)`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 14 | Longest Increasing Subsequence | Medium | [LC 300](https://leetcode.com/problems/longest-increasing-subsequence/) | dp[i] = max(dp[j]+1) for j<i, nums[j]<nums[i] | Patience sort |
| 15 | Number of Longest Increasing Subsequences | Medium | [LC 673](https://leetcode.com/problems/number-of-longest-increasing-subsequence/) | Track dp[i] and count[i] simultaneously | - |
| 16 | Maximum Sum Increasing Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/maximum-sum-increasing-subsequence-dp-14/) | dp[i] = max sum of IS ending at i | - |
| 17 | Print LIS | Medium | [GFG](https://www.geeksforgeeks.org/construction-of-longest-increasing-subsequence-using-dynamic-programming/) | Reconstruct via parent[] array | - |

### 3.5 LIS — O(n log n) Patience Sort
> **Core idea:** Maintain `tails[]` where `tails[i]` = smallest tail of IS of length i+1. Binary search for position. Length of tails = LIS length.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Longest Increasing Subsequence (Fast) | Medium | [LC 300](https://leetcode.com/problems/longest-increasing-subsequence/) | Binary search on tails[] array | - |
| 19 | Largest Divisible Subset | Medium | [LC 368](https://leetcode.com/problems/largest-divisible-subset/) | Sort + LIS where nums[j] divides nums[i] | - |
| 20 | Russian Doll Envelopes | Hard | [LC 354](https://leetcode.com/problems/russian-doll-envelopes/) | Sort by w asc, h desc → LIS on h | - |
| 21 | Make Array Strictly Increasing | Hard | [LC 1187](https://leetcode.com/problems/make-array-strictly-increasing/) | LIS with replacement: dp[i][j] = min swaps | - |

### 3.6 LIS — Bitonic (LIS + LDS Combined)
> **Core idea:** Compute LIS ending at i (L→R) AND LDS starting at i (R→L). Bitonic length through i = LIS[i]+LDS[i]-1.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 22 | Longest Bitonic Subsequence | Medium | [GFG](https://www.geeksforgeeks.org/longest-bitonic-subsequence-dp-15/) | LIS[i] + LDS[i] - 1 | - |
| 23 | Minimum Removals to Make Mountain Array | Hard | [LC 1671](https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/) | n - max(LIS[i]+LDS[i]-1) at valid peaks | - |
| 24 | Valid Mountain Array Check | Easy | [LC 941](https://leetcode.com/problems/valid-mountain-array/) | Verify single peak, both sides strictly mono | - |

### 3.7 LIS — Multi-Dimensional (Box Stacking / 3D)
> **Core idea:** Generate all rotations of 3D boxes. Sort by one dimension. Run LIS where box_j fits under box_i iff all dimensions strictly less.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Box Stacking Problem | Hard | [GFG](https://www.geeksforgeeks.org/box-stacking-problem-dp-22/) | Generate rotations, sort, run 2D LIS | - |
| 26 | Maximum Height by Stacking Cuboids | Hard | [LC 1691](https://leetcode.com/problems/maximum-height-by-stacking-cuboids/) | Sort dims within each box, sort boxes, LIS | - |

### 3.8 Edit Distance — Minimum Operations
> **Core idea:** `dp[i][j]` = min ops to convert s1[0..i-1] to s2[0..j-1]. Match→`dp[i-1][j-1]`. Else→`1+min(delete,insert,replace)`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 27 | Edit Distance | Hard | [LC 72](https://leetcode.com/problems/edit-distance/) | Classic 3-operation DP | - |
| 28 | One Edit Distance | Medium (Premium) | [LC 161](https://leetcode.com/problems/one-edit-distance/) | Check if edit_distance(s,t) == 1 | - |
| 29 | Delete Operation for Two Strings | Medium | [LC 583](https://leetcode.com/problems/delete-operation-for-two-strings/) | Special edit distance (only deletions) | LCS |
| 30 | Min Operations to Convert String | Medium | [LC 2937](https://leetcode.com/problems/minimum-number-of-operations-to-make-string-satisfying-the-given-constraint/) | Edit variant with constraints | - |

### 3.9 Pattern Matching DP (Wildcard / Regex)
> **Core idea:** `dp[i][j]` = can pattern[0..j-1] match string[0..i-1]. Handle `*`, `.` with careful base cases.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 31 | Wildcard Matching | Hard | [LC 44](https://leetcode.com/problems/wildcard-matching/) | * matches 0+ chars: dp[i][j] = dp[i][j-1] OR dp[i-1][j] | - |
| 32 | Regular Expression Matching | Hard | [LC 10](https://leetcode.com/problems/regular-expression-matching/) | * with preceding char: 0 uses or 1+ uses | - |

### 3.10 Subsequence Counting DP
> **Core idea:** `dp[i][j]` = ways to form pattern[0..j-1] as subsequence of string[0..i-1]. Match→`dp[i-1][j-1]+dp[i-1][j]`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 33 | Distinct Subsequences | Hard | [LC 115](https://leetcode.com/problems/distinct-subsequences/) | dp[i][j] = ways to form t in s | - |
| 34 | Is Subsequence | Easy | [LC 392](https://leetcode.com/problems/is-subsequence/) | 2-pointer / dp[i][j] = feasibility | - |
| 35 | Number of Matching Subsequences | Medium | [LC 792](https://leetcode.com/problems/number-of-matching-subsequences/) | Multiple targets, advance each via HashMap | - |
| 36 | Interleaving String | Medium | [LC 97](https://leetcode.com/problems/interleaving-string/) | dp[i][j] = can s1[0..i]+s2[0..j] form s3[0..i+j] | DFS+memo |
| 37 🆕 | Distinct Subsequences II | Hard | [LC 940](https://leetcode.com/problems/distinct-subsequences-ii/) | dp[c] = distinct subseq ending with char c | - |

### 3.11 Palindrome DP — Detection (Is Palindrome Precompute)
> **Core idea:** `isPalin[i][j]` = true if s[i..j] is palindrome. Precompute O(n²) using `s[i]==s[j]` and `isPalin[i+1][j-1]`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 38 | Longest Palindromic Substring | Medium | [LC 5](https://leetcode.com/problems/longest-palindromic-substring/) | Expand around center OR fill isPalin table | Manacher's |
| 39 | Palindromic Substrings Count | Medium | [LC 647](https://leetcode.com/problems/palindromic-substrings/) | Sum of all isPalin[i][j] | Manacher's |

### 3.12 Palindrome DP — Longest Palindromic Subsequence (Interval)
> **Core idea:** `dp[i][j]` = LPS in s[i..j]. s[i]==s[j]→`dp[i+1][j-1]+2`. Else→`max(dp[i+1][j],dp[i][j-1])`. Fill by increasing interval length.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 40 | Longest Palindromic Subsequence | Medium | [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/) | Classic interval DP | LCS(s,rev_s) |
| 41 | Count Different Palindromic Subsequences | Hard | [LC 730](https://leetcode.com/problems/count-different-palindromic-subsequences/) | Interval DP with 4 char states | - |
| 42 | Count Palindromic Subsequences (length 5) | Hard | [LC 2484](https://leetcode.com/problems/count-palindromic-subsequences/) | Enumerate middle char + count borders | - |

### 3.13 Palindrome DP — Partitioning (Min Cuts)
> **Core idea:** `dp[i]` = min cuts for s[0..i] to be all palindromes. `dp[i] = min(dp[i], dp[j-1]+1)` if s[j..i] is palindrome.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 43 | Palindrome Partitioning (All Partitions) | Medium | [LC 131](https://leetcode.com/problems/palindrome-partitioning/) | Backtracking + isPalin precompute | - |
| 44 | Palindrome Partitioning II (Min Cuts) | Hard | [LC 132](https://leetcode.com/problems/palindrome-partitioning-ii/) | dp[i] = min cuts using isPalin | - |
| 45 | Palindrome Partitioning III (K Partitions) | Hard | [LC 1278](https://leetcode.com/problems/palindrome-partitioning-iii/) | 2D DP: dp[k][i] = min cost for k parts in s[0..i] | - |
| 46 | Palindrome Partitioning IV (Exact 3 Parts) | Hard | [LC 1745](https://leetcode.com/problems/palindrome-partitioning-iv/) | Precompute isPalin, check all split points | - |

### 🆕 3.14 DP on Strings with Rolling Hash
> **Core idea:** DP requires checking if a substring matches some property (equals another substring, is a repeat, etc.) in O(1). Precompute polynomial rolling hashes so any substring comparison is O(1). The DP itself is standard; the hash is the enabling data structure.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Longest Chunked Palindrome Decomposition | Hard | [LC 1147](https://leetcode.com/problems/longest-chunked-palindrome-decomposition/) | Greedy/DP + polynomial hash to match prefix=suffix | - |
| 2 | Distinct Echo Substrings | Hard | [LC 1316](https://leetcode.com/problems/distinct-echo-substrings/) | Count substrings s where s=s; rolling hash + DP | - |
| 3 | Extra Characters in a String | Medium | [LC 2707](https://leetcode.com/problems/extra-characters-in-a-string/) | dp[i]+trie/hash for O(1) word lookup | Trie |

---

## 4. GRID / 2D DP

### 4.1 Grid Path — Counting Paths
> **Core idea:** `dp[i][j]` = ways to reach (i,j) from (0,0) right/down only. `dp[i][j] = dp[i-1][j]+dp[i][j-1]`. Blocked = 0.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Unique Paths | Medium | [LC 62](https://leetcode.com/problems/unique-paths/) | dp[i][j] = dp[i-1][j]+dp[i][j-1] | Math C(m+n,m) |
| 2 | Unique Paths II (With Obstacles) | Medium | [LC 63](https://leetcode.com/problems/unique-paths-ii/) | Set dp=0 at obstacle cells | - |
| 3 | Count All Paths in Grid | Easy | [GFG](https://www.geeksforgeeks.org/count-possible-paths-top-left-bottom-right-nxm-matrix/) | Basic path count DP | - |
| 4 | Number of Paths with Max Score | Hard | [LC 1301](https://leetcode.com/problems/number-of-paths-with-max-score/) | Track (max score, count) simultaneously | - |

### 4.2 Grid Path — Minimum / Maximum Cost
> **Core idea:** `dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`. Can overwrite grid in-place.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Minimum Path Sum | Medium | [LC 64](https://leetcode.com/problems/minimum-path-sum/) | dp[i][j] = grid[i][j] + min(up, left) | - |
| 6 | Triangle (Variable Width) | Medium | [LC 120](https://leetcode.com/problems/triangle/) | Bottom-up 1D DP, works in-place | - |
| 7 | Minimum Falling Path Sum | Medium | [LC 931](https://leetcode.com/problems/minimum-falling-path-sum/) | dp[i][j] = min of 3 cells above | - |
| 8 | Minimum Falling Path Sum II | Hard | [LC 1289](https://leetcode.com/problems/minimum-falling-path-sum-ii/) | Track 1st and 2nd min of previous row | - |
| 9 | Gold Mine Problem | Medium | [GFG](https://www.geeksforgeeks.org/gold-mine-problem/) | Start any row, move right only, 3 directions | - |
| 10 | Minimum Path Cost in a Grid | Medium | [LC 2304](https://leetcode.com/problems/minimum-path-cost-in-a-grid/) | dp[i][j] = min(prev row dp + moveCost) | - |
| 11 | Maximum Number of Moves in a Grid | Medium | [LC 2684](https://leetcode.com/problems/maximum-number-of-moves-in-a-grid/) | Max reachable column per row | - |

### 4.3 Grid Path — Reverse DP (Start from End)
> **Core idea:** `dp[i][j]` = min resource needed **from** (i,j) **to** end. Fill from bottom-right upward.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Dungeon Game | Hard | [LC 174](https://leetcode.com/problems/dungeon-game/) | dp[i][j] = min health needed at (i,j) to reach end | - |
| 13 | Minimum Path to the Target | Medium | [GFG](https://www.geeksforgeeks.org/min-cost-path-dp-6/) | Reverse DP variant | - |

### 4.4 Grid — 2D Prefix Sum
> **Core idea:** Precompute `prefix[i][j]`. Sum of any rectangle = O(1) via inclusion-exclusion.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 14 | Matrix Block Sum | Medium | [LC 1314](https://leetcode.com/problems/matrix-block-sum/) | Prefix sum, each cell = sum of k-radius block | - |
| 15 | Range Sum Query 2D | Medium | [LC 304](https://leetcode.com/problems/range-sum-query-2d-immutable/) | Pure 2D prefix sum queries | - |
| 16 | Number of Submatrices That Sum to Target | Hard | [LC 1074](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/) | Fix top/bottom rows, column prefix → hashmap | - |
| 17 | Count Submatrices with All Ones | Medium | [LC 2906](https://leetcode.com/problems/count-sub-matrices-with-all-ones/) | 2D prefix OR dp[i][j] = min of column runs | - |

### 4.5 Grid — Square / Rectangle DP
> **Core idea:** `dp[i][j]` = largest all-1 square with bottom-right at (i,j) = `min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Maximal Square | Medium | [LC 221](https://leetcode.com/problems/maximal-square/) | dp[i][j] = min of 3 neighbors + 1 | - |
| 19 | Count Square Submatrices with All Ones | Medium | [LC 1277](https://leetcode.com/problems/count-square-submatrices-with-all-ones/) | Same DP, answer = sum of all dp[i][j] | - |
| 20 | Maximal Rectangle | Hard | [LC 85](https://leetcode.com/problems/maximal-rectangle/) | Convert to histogram heights, then stack | Stack |
| 21 | Count Submatrices with All Ones | Hard | [LC 1504](https://leetcode.com/problems/count-submatrices-with-all-ones/) | dp[i][j] = consecutive 1s ending at j in row i | - |

### 4.6 Grid — Two-Agent Simultaneous Traversal
> **Core idea:** Two agents on same grid. State = (r1,c1,r2,c2). Since r1+c1=r2+c2, reduce to 3D: (step,r1,r2). c1=step-r1, c2=step-r2.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 22 | Cherry Pickup | Hard | [LC 741](https://leetcode.com/problems/cherry-pickup/) | 2 agents, 3D DP (step, r1, r2) | Section 4.8 |
| 23 | Cherry Pickup II | Hard | [LC 1463](https://leetcode.com/problems/cherry-pickup-ii/) | Top-down, two robots, column states | Section 4.8 |

### 4.7 Grid — DFS + Memoization (DAG on Grid)
> **Core idea:** Monotone property (strictly increasing) makes grid a DAG. DFS with memoization; each cell computed exactly once.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 24 | Longest Increasing Path in a Matrix | Hard | [LC 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | DFS+memo, increasing = no cycles | Topo sort |
| 25 | Out of Boundary Paths | Medium | [LC 576](https://leetcode.com/problems/out-of-boundary-paths/) | dp[moves][r][c] = count paths going out | DFS+memo |
| 26 🆕 | Number of Increasing Paths in a Grid | Hard | [LC 2328](https://leetcode.com/problems/number-of-increasing-paths-in-a-grid/) | Count all increasing paths via DFS+memo | Topo sort |

### 🆕 4.8 Multi-Pointer DP — Two Independent Moving Boundaries
> **Core idea:** Two or more indices are **simultaneously** part of the DP state, neither being "the position we're computing dp for." The state cannot be reduced to a single index. Common forms: dp[i][j] where (i,j) are two shrinking/expanding endpoints, or dp[step][a][b] tracking two agents. Signal: the problem requires tracking two independent "where am I" positions at once.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Cherry Pickup | Hard | [LC 741](https://leetcode.com/problems/cherry-pickup/) | dp[step][r1][r2], c derived; agents move simultaneously | 4.6 |
| 2 | Cherry Pickup II | Hard | [LC 1463](https://leetcode.com/problems/cherry-pickup-ii/) | dp[row][c1][c2]; two robots, different cols | 4.6 |
| 3 | Longest Palindromic Subsequence | Medium | [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/) | dp[i][j] = LPS in s[i..j]; (i,j) shrink inward | 3.12 |
| 4 | Minimum Cost to Make Array Palindrome | Medium | [GFG](https://www.geeksforgeeks.org/minimum-cost-to-make-string-palindrome/) | dp[i][j] with i,j as two boundary pointers | - |
| 5 | Longest Chunked Palindrome Decomp | Hard | [LC 1147](https://leetcode.com/problems/longest-chunked-palindrome-decomposition/) | (lo, hi) pointers meet in middle | 3.14 |
| 6 | Zuma Game | Hard | [LC 488](https://leetcode.com/problems/zuma-game/) | dp[i][j][k] — interval + extra state count | 5.1 |
| 7 | Count Palindromic Subsequences | Hard | [LC 2484](https://leetcode.com/problems/count-palindromic-subsequences/) | Multiple anchor indices tracked simultaneously | 3.12 |

---

## 5. INTERVAL DP

### 5.1 Interval DP — Classic Merge / Split (MCM Pattern)
> **Core idea:** `dp[i][j]` = optimal cost for subproblem on [i,j]. Try all split k: `dp[i][j] = min over k(dp[i][k]+dp[k+1][j]+cost(i,j,k))`. Fill by increasing interval length.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Matrix Chain Multiplication | Hard | [GFG](https://www.geeksforgeeks.org/matrix-chain-multiplication-dp-8/) | Classic MCM, cost = dims product | - |
| 2 | Minimum Cost to Merge Stones | Hard | [LC 1000](https://leetcode.com/problems/minimum-cost-to-merge-stones/) | Merge K piles; valid if (n-1)%(k-1)==0 | - |
| 3 | Minimum Cost to Cut a Stick | Hard | [LC 1547](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/) | dp[i][j] = min cost to make all cuts in [i,j] | Knuth's O(n²), 17.7 |
| 4 | Optimal Binary Search Tree | Hard | [GFG](https://www.geeksforgeeks.org/optimal-binary-search-tree-dp-24/) | dp[i][j] = min search cost for keys i..j | Knuth's O(n²), 17.7 |
| 5 | Minimum Score Triangulation of Polygon | Medium | [LC 1039](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/) | dp[i][j] = min cost to triangulate polygon i..j | - |
| 6 | Zuma Game | Hard | [LC 488](https://leetcode.com/problems/zuma-game/) | dp on string intervals with state | - |
| 7 🆕 | Score of Students Solving Math Expression | Hard | [LC 2019](https://leetcode.com/problems/the-score-of-students-solving-math-expression/) | Interval DP tracking set of possible values | - |

### 5.2 Interval DP — Reverse Thinking (Last Operation)
> **Core idea:** Think about the **last** operation instead of first. "What was the last balloon burst?" → neighbors are i and j (the borders).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Burst Balloons | Hard | [LC 312](https://leetcode.com/problems/burst-balloons/) | dp[i][j] = max coins, k = LAST burst in (i,j) | - |
| 9 | Strange Printer | Hard | [LC 664](https://leetcode.com/problems/strange-printer/) | dp[i][j] = min turns to print s[i..j] | - |
| 10 | Remove Boxes | Hard | [LC 546](https://leetcode.com/problems/remove-boxes/) | dp[i][j][k] = max points with k extra boxes | - |
| 11 | Strange Printer II (Colors) | Hard | [LC 1591](https://leetcode.com/problems/strange-printer-ii/) | Build color containment DAG → check topo sort | - |

### 5.3 Interval DP — Palindrome Structure
> **Core idea:** `dp[i][j]` depends on `dp[i+1][j-1]`. If s[i]==s[j]: extend inward. Fill from small to large intervals.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Longest Palindromic Subsequence | Medium | [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/) | dp[i][j]: match borders → dp[i+1][j-1]+2 | LCS |
| 13 | Palindrome Partitioning II | Hard | [LC 132](https://leetcode.com/problems/palindrome-partitioning-ii/) | isPalin interval DP + cut DP | - |
| 14 | Count Different Palindromic Subsequences | Hard | [LC 730](https://leetcode.com/problems/count-different-palindromic-subsequences/) | Interval DP with 4 character cases | - |

### 5.4 Game Theory DP — Minimax (Optimal Play)
> **Core idea:** `dp[i][j]` = score diff (current - other) for subgame [i,j]. Current player maximizes dp[i][j].

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Predict the Winner | Medium | [LC 486](https://leetcode.com/problems/predict-the-winner/) | dp[i][j] = max score diff for current player | - |
| 16 | Stone Game | Medium | [LC 877](https://leetcode.com/problems/stone-game/) | First player always wins (math), or minimax | Math |
| 17 | Stone Game V | Hard | [LC 1563](https://leetcode.com/problems/stone-game-v/) | Split, loser gets left or right remaining | - |
| 18 | Stone Game VII | Medium | [LC 1690](https://leetcode.com/problems/stone-game-vii/) | Pick sides, score = remaining sum - picked | - |
| 19 | Guess Number Higher or Lower II | Medium | [LC 375](https://leetcode.com/problems/guess-number-higher-or-lower-ii/) | Minimax: dp[i][j] = min guaranteed cost | - |

### 5.5 Game Theory DP — Prefix/Suffix Optimization
> **Core idea:** `dp[i]` = suffix DP (best score from index i onward). Often reducible to suffix array operations.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 20 | Stone Game II | Medium | [LC 1140](https://leetcode.com/problems/stone-game-ii/) | dp[i][m] = max piles from i onward with M piles | - |
| 21 | Stone Game III | Hard | [LC 1406](https://leetcode.com/problems/stone-game-iii/) | dp[i] = max score from i picking 1,2,3 | - |
| 22 | Stone Game IV | Hard | [LC 1510](https://leetcode.com/problems/stone-game-iv/) | dp[n] = can current player win with n stones? | - |
| 23 | Stone Game VIII | Hard | [LC 1872](https://leetcode.com/problems/stone-game-viii/) | Suffix DP, pick prefix sum | - |
| 24 | Stone Game IX | Medium | [LC 2029](https://leetcode.com/problems/stone-game-ix/) | Modulo 3 grouping + counting | - |

### 5.6 Game Theory DP — Bitmask Can-I-Win
> **Core idea:** State = bitmask of numbers already chosen. `dp[mask]` = can current player win given `mask` of used numbers.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 25 | Can I Win | Medium | [LC 464](https://leetcode.com/problems/can-i-win/) | dp[mask] = first player wins from this state? | - |
| 26 | Flip Game II | Medium (Premium) | [LC 294](https://leetcode.com/problems/flip-game-ii/) | Bitmask game DP | Sprague-Grundy |

---

## 6. PARTITION DP

### 6.1 Partition — Fixed Window Optimization
> **Core idea:** `dp[i]` = optimal for array[0..i]. Look back up to k steps: `dp[i] = opt over j in [i-k..i] of (dp[j-1]+cost(j,i))`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Partition Array for Maximum Sum | Medium | [LC 1043](https://leetcode.com/problems/partition-array-for-maximum-sum/) | dp[i] = max(dp[i-k]+max_in_window*k) | - |
| 2 | Largest Sum of Averages | Medium | [LC 813](https://leetcode.com/problems/largest-sum-of-averages/) | dp[k][i] = max avg with k groups in [0..i] | - |
| 3 | Maximum Profit in Job Scheduling | Hard | [LC 1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/) | Binary search for non-overlapping + dp | Segment tree |

### 6.2 Partition — K Groups, Minimize Maximum (Binary Search + DP)
> **Core idea:** Binary search on the answer (max allowed). For each candidate, greedily check if ≤K groups suffice.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | Split Array Largest Sum | Hard | [LC 410](https://leetcode.com/problems/split-array-largest-sum/) | Binary search on max sum → greedy check | DP O(n²k) |
| 5 | Painters Partition Problem | Hard | [GFG](https://www.geeksforgeeks.org/painters-partition-problem/) | Binary search on max paint → check k painters | - |
| 6 | Allocate Minimum Number of Pages | Hard | [GFG](https://www.geeksforgeeks.org/allocate-minimum-number-pages/) | Binary search on max pages per student | - |
| 7 | Minimum Difficulty of a Job Schedule | Hard | [LC 1335](https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/) | dp[d][i] = min difficulty doing d days, jobs 0..i | - |

### 6.3 Partition — Sliding Window DP (Deque Optimization)
> **Core idea:** `dp[i]` from window of previous dp values. Monotonic deque maintains max/min in O(1). Reduces O(n²) to O(n).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Jump Game VI | Medium | [LC 1696](https://leetcode.com/problems/jump-game-vi/) | dp[i] = max(dp[i-k..i-1]) + nums[i], deque | Segment tree |
| 9 | Sliding Window Maximum | Hard | [LC 239](https://leetcode.com/problems/sliding-window-maximum/) | Monotone deque for range max in O(n) | - |
| 10 | Constrained Subsequence Sum | Hard | [LC 1425](https://leetcode.com/problems/constrained-subsequence-sum/) | dp[i] = nums[i] + max(dp[i-k..i-1]), deque | - |

### 6.4 Egg Drop — 2D DP + Binary Search Optimization
> **Core idea:** `dp[t][e]` = max floors testable with t trials and e eggs = `dp[t-1][e-1]+1+dp[t-1][e]`. Find min t where dp[t][K]≥N.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Egg Drop Problem | Hard | [GFG](https://www.geeksforgeeks.org/egg-dropping-puzzle-dp-11/) | dp[e][f] = 1 + min over x of max(dp[e-1][x-1], dp[e][f-x]) | - |
| 12 | Super Egg Drop | Hard | [LC 887](https://leetcode.com/problems/super-egg-drop/) | Inverted DP: dp[t][k] = max floors tested | Binary search |

### 6.5 Jump Game Family (DP / Greedy Boundary)
> **Core idea:** `dp[i]` = can we reach i? Or: min jumps? Greedy when jump as far as possible works. DP/BFS for complex constraints.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 13 | Jump Game I | Medium | [LC 55](https://leetcode.com/problems/jump-game/) | Greedy: track max_reach | DP |
| 14 | Jump Game II | Medium | [LC 45](https://leetcode.com/problems/jump-game-ii/) | Greedy BFS: expand layer by layer | DP |
| 15 | Jump Game VII | Medium | [LC 1871](https://leetcode.com/problems/jump-game-vii/) | dp[i] = can we reach i? Prefix sum of dp | - |
| 16 | Frog Jump | Hard | [LC 403](https://leetcode.com/problems/frog-jump/) | dp[stone][k] = can we reach stone with jump k | - |
| 17 | Minimum Number of Taps to Water Garden | Hard | [LC 1326](https://leetcode.com/problems/minimum-number-of-taps-to-open-to-water-a-garden/) | Transform to Jump Game II | Greedy |

### 🆕 6.6 Partition DP — Non-Contiguous Assignment (People to Groups)
> **Core idea:** Assign n items to exactly k **non-ordered** groups (not contiguous partitions of a sequence). `dp[mask]` or `dp[i][j]` = min cost assigning a subset. Unlike contiguous partition, any assignment is valid. Often uses bitmask DP when n is small.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Minimum Number of Work Sessions | Hard | [LC 1986](https://leetcode.com/problems/minimum-number-of-work-sessions-to-finish-the-tasks/) | Bitmask DP: dp[mask] = min sessions to complete tasks in mask | - |
| 2 | Minimum Total Distance Traveled | Hard | [LC 2463](https://leetcode.com/problems/minimum-total-distance-traveled/) | DP: assign robots to factories; sort both first | - |
| 3 | Fair Distribution of Cookies | Medium | [LC 2305](https://leetcode.com/problems/fair-distribution-of-cookies/) | Backtracking + bitmask; dp[child][mask] | Bitmask DP |

---

## 7. STOCK MARKET DP — STATE MACHINE

### 7.1 Stock — Fixed Transaction Limit (State Machine)
> **Core idea:** States: `hold` and `cash`. `hold[i]=max(hold[i-1], cash[i-1]-price[i])`. `cash[i]=max(cash[i-1], hold[i-1]+price[i])`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Best Time to Buy & Sell Stock I | Easy | [LC 121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) | One transaction: track min price so far | Greedy |
| 2 | Best Time to Buy & Sell Stock II | Medium | [LC 122](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) | Unlimited: hold/cash state machine | Greedy |
| 3 | Best Time to Buy & Sell Stock III | Hard | [LC 123](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) | 4 states: buy1, sell1, buy2, sell2 | - |
| 4 | Best Time to Buy & Sell Stock IV | Hard | [LC 188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) | 2k states OR dp[k][0/1] for k transactions | - |

### 7.2 Stock — With Cooldown (Extra Rest State)
> **Core idea:** `cooldown[i]=hold[i-1]+price[i]`. `hold[i]=max(hold[i-1], rest[i-1]-price[i])`. `rest[i]=max(rest[i-1], cooldown[i-1])`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Best Time to Buy & Sell with Cooldown | Medium | [LC 309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) | 3 states: held, sold(cooldown), rest | - |

### 7.3 Stock — With Transaction Fee
> **Core idea:** When selling, subtract fee. `cash[i]=max(cash[i-1], hold[i-1]+price[i]-fee)`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Best Time to Buy & Sell with Fee | Medium | [LC 714](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/) | cash = max(cash, hold+price-fee) | Greedy |

---

## 8. BITMASK DP

### 8.1 Bitmask DP — TSP / Visit All Nodes
> **Core idea:** `dp[mask][i]` = optimal cost visiting exactly nodes in `mask`, ending at node i. O(2^n * n²).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Travelling Salesman Problem | Hard | [GFG](https://www.geeksforgeeks.org/travelling-salesman-problem-set-1/) | dp[mask][i] = min cost, visited mask, at city i | - |
| 2 | Shortest Path Visiting All Nodes | Hard | [LC 847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) | BFS with state (node, visited_mask) | Dijkstra |
| 3 | Find Shortest Path to Reach All Nodes | Hard | [GFG](https://www.geeksforgeeks.org/shortest-path-to-visit-all-the-nodes-of-a-graph/) | Bitmask BFS, multi-source | - |

### 8.2 Bitmask DP — Assignment / Matching
> **Core idea:** Assign n people to n tasks. `dp[mask]` = optimal cost. Person = popcount(mask)-1. Try all tasks j in mask.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | Assignment Problem | Hard | [GFG](https://www.geeksforgeeks.org/assignment-problem-using-bitmask/) | dp[mask] = min cost assigning popcount(mask) people | Hungarian |
| 5 | Minimum XOR Sum of Two Arrays | Hard | [LC 1879](https://leetcode.com/problems/minimum-xor-sum-of-two-arrays/) | dp[mask] = min XOR assigning nums2 to nums1 | Hungarian |
| 6 | Minimum Cost to Connect Two Groups | Hard | [LC 1595](https://leetcode.com/problems/minimum-cost-to-connect-two-groups-of-points/) | dp[i][mask] = min cost, row i, group2 covered = mask | - |
| 7 | Maximize Score After N Operations | Hard | [LC 1799](https://leetcode.com/problems/maximize-score-after-n-operations/) | dp[mask] = max score, pairs chosen = mask | - |

### 8.3 Bitmask DP — Skill Coverage (Subset Cover)
> **Core idea:** `dp[mask]` = min people to cover all skills in mask. `dp[mask|s] = min(dp[mask]+1)`. Answer = dp[(1<<n)-1].

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Smallest Sufficient Team | Hard | [LC 1125](https://leetcode.com/problems/smallest-sufficient-team/) | dp[mask] = min team covering skills in mask | - |
| 9 | Stickers to Spell Word | Hard | [LC 691](https://leetcode.com/problems/stickers-to-spell-word/) | dp[mask] = min stickers to cover chars in mask | BFS |
| 10 🆕 | Count Square-Free Subsets | Hard | [LC 2572](https://leetcode.com/problems/count-the-number-of-square-free-subsets/) | Bitmask DP over prime factors; dp[mask] = count | - |

### 8.4 Bitmask DP — Row-by-Row Profile DP
> **Core idea:** State = bitmask of current row's configuration. For each row, enumerate all valid masks, transition from previous row's valid masks.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Maximum Students Taking Exam | Hard | [LC 1349](https://leetcode.com/problems/maximum-students-taking-exam/) | dp[row][mask] = max students, row filled = mask | - |
| 12 | Number of Ways to Paint N×3 Grid | Hard | [LC 1411](https://leetcode.com/problems/number-of-ways-to-paint-n-3-grid/) | Count valid colorings row by row | Matrix exp |

### 8.5 Bitmask DP — Hat/Item Distribution
> **Core idea:** `dp[mask of people with hats]` = ways. Iterate hats; try assigning to each unhatted person. `dp[mask|(1<<p)] += dp[mask]`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 13 | Number of Ways to Wear Different Hats | Hard | [LC 1434](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/) | Iterate hats outer, people inner, mask = people with hats | - |
| 14 | Distribute Repeating Integers | Hard | [LC 1655](https://leetcode.com/problems/distribute-repeating-integers/) | dp[mask of satisfied customers] = feasibility | - |

### 8.6 Bitmask DP — Permutation Counting
> **Core idea:** `dp[mask]` = count of permutations of elements in mask where each new element satisfies condition with the last.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Number of Squareful Arrays | Hard | [LC 996](https://leetcode.com/problems/number-of-squareful-arrays/) | dp[mask][last] = count perms, adj sum = perfect square | - |
| 16 | Find Minimum Time to Finish All Jobs | Hard | [LC 1723](https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/) | dp[mask] = min max-time assigning jobs in mask to k workers | Backtracking |
| 17 🆕 | Special Permutations | Medium | [LC 2741](https://leetcode.com/problems/special-permutations/) | dp[mask][last] = count perms where adj pair is divisible | - |

### 8.7 Bitmask DP — Topo Ordering with Prerequisites
> **Core idea:** `dp[mask]` = min semesters to complete courses in mask. Course unlocked when all prerequisites are in mask.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 18 | Parallel Courses II | Hard | [LC 1494](https://leetcode.com/problems/parallel-courses-ii/) | dp[mask] = min terms, take subset of unlocked per term | - |

### 8.8 Bitmask DP — AND/OR Optimization
> **Core idea:** `dp[mask]` maximizes an AND or OR aggregate over slots. Assign values to positions, track used.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 19 | Maximum AND Sum of Array | Hard | [LC 2172](https://leetcode.com/problems/maximum-and-sum-of-array/) | dp[mask] = max AND sum, slots used = mask | - |

---

## 9. DIGIT DP

### 9.1 Digit DP — Count Numbers with Digit Constraint (Tight Bound)
> **Core idea:** Build digit by digit from MSB. State=(position, tight, extra). `tight`=current prefix equals bound. If not tight, any digit 0-9 valid.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Count Numbers with Unique Digits | Medium | [LC 357](https://leetcode.com/problems/count-numbers-with-unique-digits/) | Digit DP or combinatorics | Combinatorics |
| 2 | Count Special Integers | Hard | [LC 2376](https://leetcode.com/problems/count-special-integers/) | State=(pos, tight, used_mask) | - |
| 3 | Numbers At Most N Given Digit Set | Hard | [LC 902](https://leetcode.com/problems/numbers-at-most-n-given-digit-set/) | Count valid numbers with digits from set | - |
| 4 | Digit Count in Range | Hard | [LC 1067](https://leetcode.com/problems/digit-count-in-range/) | Count occurrences of digit d in [low, high] | - |
| 5 | Count Numbers with Sum of Digits = K | Medium | [GFG](https://www.geeksforgeeks.org/count-of-numbers-from-1-to-n-having-sum-of-digits-as-k/) | State=(pos, tight, current_sum) | - |
| 6 🆕 | Count Integers (digit sum in [a,b]) | Hard | [LC 2719](https://leetcode.com/problems/count-of-integers/) | State=(pos, tight, sum_so_far) | - |
| 7 🆕 | Count the Number of Powerful Integers | Hard | [LC 2999](https://leetcode.com/problems/count-the-number-of-powerful-integers/) | State=(pos, tight, suffix_matched) | - |

### 9.2 Digit DP — Non-Consecutive / Pattern Constraint
> **Core idea:** State tracks the **last digit placed** to enforce no-consecutive rule. `dp[pos][last_digit][tight]`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Non-negative Integers without Consecutive Ones | Hard | [LC 600](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/) | Track last bit: no two consecutive 1s | - |
| 9 | Rotated Digits (Valid Numbers) | Medium | [LC 788](https://leetcode.com/problems/rotated-digits/) | Digit DP: track if any valid digit placed | - |
| 10 | Numbers with Same First and Last Digit | Medium | [GFG](https://www.geeksforgeeks.org/count-n-digit-numbers-whose-first-last-digits-are-x-y/) | State tracks first digit placed | - |
| 11 🆕 | Numbers with Repeated Digits | Hard | [LC 1012](https://leetcode.com/problems/numbers-with-repeated-digits/) | Count by complement: total - no-repeat; state=(pos, tight, used_mask) | - |

### 9.3 Digit DP — Divisibility Constraint
> **Core idea:** State includes current number mod M. `dp[pos][tight][remainder]`. `new_rem=(rem*10+digit)%M`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 12 | Count of Numbers Divisible by X | Medium | [GFG](https://www.geeksforgeeks.org/count-numbers-1-n-divisible-x/) | State=(pos, tight, mod) | Math |
| 13 | Number of Digit One | Hard | [LC 233](https://leetcode.com/problems/number-of-digit-one/) | Count 1s in all numbers 1..n | Digit DP |
| 14 | Digit DP Template | Hard | [GFG](https://www.geeksforgeeks.org/digit-dp-introduction/) | General framework | - |
| 15 🆕 | Number of Beautiful Integers in Range | Hard | [LC 2827](https://leetcode.com/problems/number-of-beautiful-integers-in-the-range/) | State=(pos, tight, even-odd diff, rem mod k) | - |

---

## 10. TREE DP

### 10.1 Tree DP — Single Pass Return (Subtree Aggregate)
> **Core idea:** DFS returns a value from each subtree. Parent combines children. Solve children first (post-order).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Diameter of Binary Tree | Easy | [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/) | ans=max(ans,left+right); return max(left,right)+1 | - |
| 2 | Binary Tree Maximum Path Sum | Hard | [LC 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | ans=max(ans,left+right+val); return max arm | - |
| 3 | Longest Univalue Path | Medium | [LC 687](https://leetcode.com/problems/longest-univalue-path/) | Extend arm only if same value | - |
| 4 | Longest Path with Different Adjacent Chars | Hard | [LC 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Top-2 arms with different char | - |
| 5 | Distribute Coins in Binary Tree | Medium | [LC 979](https://leetcode.com/problems/distribute-coins-in-binary-tree/) | Flow = |subtree_coins - subtree_nodes| | - |

### 10.2 Tree DP — Include/Exclude Current Node (Rob Pattern)
> **Core idea:** At each node, compute `rob` (take, skip children) and `skip` (don't take, children free). Return both.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | House Robber III | Medium | [LC 337](https://leetcode.com/problems/house-robber-iii/) | Return (rob_this, skip_this) pair | - |
| 7 | Binary Tree Cameras | Hard | [LC 968](https://leetcode.com/problems/binary-tree-cameras/) | 3 states: covered_no_cam, has_cam, uncovered | Greedy |
| 8 | Minimize the Total Price of Trips | Hard | [LC 2646](https://leetcode.com/problems/minimize-the-total-price-of-the-trips/) | Count trips per node → rob-style halving | - |

### 10.3 Tree DP — Subtree Sum / Product
> **Core idea:** Compute running aggregate (sum, XOR, count) for each subtree. Use to answer per-node queries or optimize global metric.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Maximum Product of Splitted Binary Tree | Medium | [LC 1339](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/) | subtree_sum * (total - subtree_sum) | - |
| 10 | Count Nodes Equal to Average of Subtree | Medium | [LC 2265](https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/) | Return (sum, count) from each subtree | - |
| 11 | Maximum Number of K-Divisible Components | Hard | [LC 2872](https://leetcode.com/problems/maximum-number-of-k-divisible-components/) | Cut edge if subtree_sum % k == 0 | - |
| 12 | Minimum Score After Removals on a Tree | Hard | [LC 2538](https://leetcode.com/problems/minimum-score-after-removals-on-a-tree/) | XOR subtree + in/out time for subset detection | - |
| 13 🆕 | Maximum Sum BST in Binary Tree | Hard | [LC 1373](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/) | Return (min,max,sum,isBST) from each subtree | - |
| 14 🆕 | Number of Nodes in Sub-Tree with Same Label | Medium | [LC 1519](https://leetcode.com/problems/number-of-nodes-in-the-sub-tree-with-the-same-label/) | Count label freq in subtree; DFS return freq array | - |

### 10.4 Tree DP — Re-rooting (Two-Pass DP)
> **Core idea:** Pass 1 (bottom-up): assume node 0 is root. Pass 2 (top-down): re-adjust each node using parent's values.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Sum of Distances in Tree | Hard | [LC 834](https://leetcode.com/problems/sum-of-distances-in-tree/) | ans[v] = ans[u] - size[v] + (n - size[v]) | - |
| 16 | Count Number of Possible Root Nodes | Hard | [LC 2581](https://leetcode.com/problems/count-number-of-possible-root-nodes/) | Re-root: edges flip direction, track valid edges | - |
| 17 | All Possible Full Binary Trees | Medium | [LC 894](https://leetcode.com/problems/all-possible-full-binary-trees/) | dp[n] = all full BTs with n nodes | - |
| 18 🆕 | Amount of Time for Tree to Be Infected | Medium | [LC 2385](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/) | Convert tree to graph → BFS; re-root thinking for max time | BFS |

### 10.5 Tree DP — Diameter / Longest Path Variants
> **Core idea:** Longest path passes through exactly one "bend" node. At each node, combine top-2 arm lengths.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 19 | Diameter of Binary Tree | Easy | [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/) | Classic: left+right at each node | - |
| 20 | Minimum Fuel Cost to Report to Capital | Medium | [LC 2477](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/) | ceil(subtree_size/seats) per edge | - |
| 21 | Longest Path with Different Adjacent Chars | Hard | [LC 2246](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/) | Extend only if char differs | - |

### 10.6 Tree DP — Leaf Value Minimization (Interval + Tree DP)
> **Core idea:** Build binary tree with given leaves. Internal nodes = product of max children leaves. Minimize total internal node cost.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 22 | Minimum Cost Tree from Leaf Values | Medium | [LC 1130](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/) | Interval DP or monotone stack | Greedy + stack |

---

## 11. DP ON GRAPHS / DAG

### 11.1 DAG DP — Longest / Shortest Path
> **Core idea:** Topological sort. Process in topo order. `dp[v] = opt over edges (u→v) of (dp[u]+weight)`.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Longest Path in a DAG | Medium | [GFG](https://www.geeksforgeeks.org/find-longest-path-directed-acyclic-graph/) | Topo + dp[v] = max(dp[u] + w) | DFS+memo |
| 2 | Shortest Path in a DAG | Medium | [GFG](https://www.geeksforgeeks.org/shortest-path-for-directed-acyclic-graphs/) | Topo + dp[v] = min(dp[u] + w) | - |
| 3 | Parallel Courses III | Hard | [LC 2050](https://leetcode.com/problems/parallel-courses-iii/) | Topo + dp[v] = max(dp[prereq]) + time[v] | - |
| 4 🆕 | Largest Color Value in Directed Graph | Hard | [LC 1857](https://leetcode.com/problems/largest-color-value-in-a-directed-graph/) | Topo + dp[v][c] = max count of color c on path to v | - |

### 11.2 DAG DP — Count Paths
> **Core idea:** `dp[v]` = number of paths from source to v. `dp[v] = sum(dp[u])` for all u→v. Process in topo order.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Count All Paths Source to Destination | Medium | [GFG](https://www.geeksforgeeks.org/count-all-possible-paths-from-top-left-to-bottom-right/) | Topo + dp[v] = sum(dp[u]) | - |
| 6 | Number of Ways to Arrive at Destination | Medium | [LC 1976](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/) | Dijkstra + count[] alongside dist[] | - |
| 7 | Number of Restricted Paths | Medium | [LC 1786](https://leetcode.com/problems/number-of-restricted-paths-from-first-to-last-node/) | Dijkstra from end → dp on DAG implied by dist | - |
| 8 🆕 | Number of Increasing Paths in a Grid | Hard | [LC 2328](https://leetcode.com/problems/number-of-increasing-paths-in-a-grid/) | Grid = DAG (increasing edges); DFS+memo count paths | Topo sort |

### 11.3 DAG DP — DP with Time/Cost State
> **Core idea:** State includes extra dimension beyond node: (node, time_remaining) or (node, cost_spent).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Minimum Cost to Reach Destination in Time | Hard | [LC 1928](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/) | dp[t][node] = min fee, t steps taken | Dijkstra |
| 10 | Longest Increasing Path in a Matrix | Hard | [LC 329](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) | Grid → DAG (increasing = directed edges) | Topo sort |

---

## 12. STATE MACHINE DP

### 12.1 State Machine — Fixed States (Attendance / Vowel Sequences)
> **Core idea:** Explicit states from problem rules. `dp[i][state]` = count of valid sequences of length i ending in state.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Student Attendance Record II | Hard | [LC 552](https://leetcode.com/problems/student-attendance-record-ii/) | States: (A_count, trailing_L_count) | Matrix exp |
| 2 | Count Vowels Permutation | Hard | [LC 1220](https://leetcode.com/problems/count-vowels-permutation/) | State = last vowel placed, transitions by rules | Matrix exp |
| 3 | Dice Roll Simulation | Hard | [LC 1223](https://leetcode.com/problems/dice-roll-simulation/) | State = (last_face, consecutive_count) | - |
| 4 | Number of Music Playlists | Hard | [LC 920](https://leetcode.com/problems/number-of-music-playlists/) | dp[i][j] = playlists of length i with j unique songs | - |

### 12.2 State Machine — Two-State Toggle (Even/Odd, On/Off)
> **Core idea:** Two alternating states. Track two running values, toggle at each element.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Ways to Make a Fair Array | Medium | [LC 1664](https://leetcode.com/problems/ways-to-make-a-fair-array/) | Track even/odd prefix sums, simulate removal | - |
| 6 | Maximum Alternating Subsequence Sum | Medium | [LC 1911](https://leetcode.com/problems/maximum-alternating-subsequence-sum/) | dp_even, dp_odd toggle at each element | - |
| 7 | Number of Ways to Rearrange Sticks | Hard | [LC 1866](https://leetcode.com/problems/number-of-ways-to-rearrange-sticks-with-k-sticks-visible/) | Stirling numbers / recurrence with visible count | - |

### 12.3 State Machine — Paint / Color Sequence
> **Core idea:** `dp[i][c]` = optimal cost painting house i with color c. Transition: min/max over all valid previous colors.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 8 | Paint House I | Medium (Premium) | [LC 256](https://leetcode.com/problems/paint-house/) | dp[i][c] = cost[i][c] + min(dp[i-1][other colors]) | - |
| 9 | Paint House II (k Colors) | Hard (Premium) | [LC 265](https://leetcode.com/problems/paint-house-ii/) | Track 1st and 2nd min to do O(nk) | - |
| 10 | Paint House III | Hard | [LC 1473](https://leetcode.com/problems/paint-house-iii/) | dp[i][c][nb] = cost with i houses, color c, nb neighborhoods | - |
| 11 | Paint Fence | Medium (Premium) | [LC 276](https://leetcode.com/problems/paint-fence/) | same[i] = prev_same, diff[i] = (k-1)*(same+diff) | - |

---

## 13. PROBABILITY & EXPECTATION DP

### 13.1 Probability DP — Forward (Compute Future Probability)
> **Core idea:** `dp[step][state]` = probability of being in state after step moves. Initialize start state = 1.0. Spread to neighbors.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Knight Probability in Chessboard | Medium | [LC 688](https://leetcode.com/problems/knight-probability-in-chessboard/) | dp[k][r][c] = prob at (r,c) after k moves | - |
| 2 | Out of Boundary Paths | Medium | [LC 576](https://leetcode.com/problems/out-of-boundary-paths/) | dp[moves][r][c] = count of paths going out | - |
| 3 | Soup Servings | Medium | [LC 808](https://leetcode.com/problems/soup-servings/) | dp[a][b] = prob A empties first | Math (large n) |

### 13.2 Probability DP — Backward (Compute Expected Value)
> **Core idea:** `dp[state]` = expected value **from** this state. Backward induction from terminal states.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 4 | New 21 Game | Medium | [LC 837](https://leetcode.com/problems/new-21-game/) | Sliding window on probability distribution | - |
| 5 | Probability of Two Boxes with Same Distinct Balls | Hard | [LC 1467](https://leetcode.com/problems/probability-of-a-two-boxes-having-the-same-number-of-distinct-balls/) | DP + combinatorics for equal-distribution count | - |
| 6 | Coin Toss Probability | Medium | [GFG](https://www.geeksforgeeks.org/coin-toss-probability-problem/) | P(exactly k heads in n flips) | Binomial |
| 7 | Dice Roll Simulation | Hard | [LC 1223](https://leetcode.com/problems/dice-roll-simulation/) | DP count sequences with consecutive face limit | - |

---

## 14. PARTITION / COUNTING DP (COMBINATORICS)

### 14.1 Partition Numbers — Integer Partition
> **Core idea:** Count ways to write n as ordered/unordered sums. Unordered → unbounded knapsack. Ordered → different recurrence.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Integer Partition (Count Ways) | Medium | [GFG](https://www.geeksforgeeks.org/partition-given-set-into-k-subsets-equal-sum/) | dp[i][j] = ways to partition i into j parts | - |
| 2 | Combination Sum IV | Medium | [LC 377](https://leetcode.com/problems/combination-sum-iv/) | Ordered sums (permutations): target outer, items inner | - |
| 3 | Count Ways to Build Good Strings | Medium | [LC 2466](https://leetcode.com/problems/count-ways-to-build-good-strings/) | dp[i] += dp[i-zero] + dp[i-one] | - |
| 4 | Number of Dice Rolls with Target Sum | Medium | [LC 1155](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/) | dp[d][t] = ways to roll d dice summing to t | - |

### 14.2 Counting DP — Sequences with Constraints
> **Core idea:** `dp[i]` = count of valid sequences of length i. Each transition checks constraint for new element.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Count Vowels Permutation | Hard | [LC 1220](https://leetcode.com/problems/count-vowels-permutation/) | State = last vowel, defined transitions | Matrix exp |
| 6 | Student Attendance Record II | Hard | [LC 552](https://leetcode.com/problems/student-attendance-record-ii/) | States track A_count and trailing L_count | Matrix exp |
| 7 | Distinct Subsequences II | Hard | [LC 940](https://leetcode.com/problems/distinct-subsequences-ii/) | dp[c] = distinct subseq ending with char c | - |
| 8 | Number of Ways to Rearrange Sticks | Hard | [LC 1866](https://leetcode.com/problems/number-of-ways-to-rearrange-sticks-with-k-sticks-visible/) | dp[n][k] = dp[n-1][k-1] + (n-1)*dp[n-1][k] | - |

---

## 15. DP WITH DATA STRUCTURES

### 15.1 DP + Binary Search (Optimize Transition Lookup)
> **Core idea:** `dp[i]` needs best dp[j] where j satisfies monotone condition. Binary search for j in O(log n).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Maximum Profit in Job Scheduling | Hard | [LC 1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/) | Sort by end time, binary search for latest non-overlap | Segment tree |
| 2 | Weighted Job Scheduling | Hard | [GFG](https://www.geeksforgeeks.org/weighted-job-scheduling/) | Sort + binary search DP | - |
| 3 | LIS O(n log n) | Medium | [LC 300](https://leetcode.com/problems/longest-increasing-subsequence/) | Binary search on tails[] array | - |
| 4 | Non-overlapping Intervals | Medium | [LC 435](https://leetcode.com/problems/non-overlapping-intervals/) | Greedy sort by end / DP | Greedy |

### 15.2 DP + Segment Tree / BIT (Range Query in Transition)
> **Core idea:** `dp[i]` needs best dp[j] over a range. Segment Tree or BIT: range max/min in O(log n).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 5 | Count of Smaller Numbers After Self | Hard | [LC 315](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) | BIT / merge sort for inversions | Merge sort |
| 6 | Count of Range Sum | Hard | [LC 327](https://leetcode.com/problems/count-of-range-sum/) | Merge sort on prefix sums | Segment tree |
| 7 | Reverse Pairs | Hard | [LC 493](https://leetcode.com/problems/reverse-pairs/) | Merge sort + DP inversion count | BIT |
| 8 | Maximum Sum of 3 Non-Overlapping Subarrays | Hard | [LC 689](https://leetcode.com/problems/maximum-sum-of-3-non-overlapping-subarrays/) | DP with prefix max left/right arrays | - |
| 9 🆕 | Longest Increasing Subsequence II | Hard | [LC 2407](https://leetcode.com/problems/longest-increasing-subsequence-ii/) | LIS where gap ≤ k; segment tree for range max dp query | - |
| 10 🆕 | Create Sorted Array through Instructions | Hard | [LC 1649](https://leetcode.com/problems/create-sorted-array-through-instructions/) | BIT to count smaller/greater on the left | Merge sort |

### 15.3 DP + Monotone Stack (Optimize Concave/Convex Transitions)
> **Core idea:** `dp[i]` depends on `dp[j]+cost(j,i)` where cost is monotone. Monotone stack reduces O(n²) to O(n).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 11 | Minimum Cost Tree from Leaf Values | Medium | [LC 1130](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/) | Greedy: eliminate smallest leaf | Interval DP |
| 12 | Sum of Subarray Minimums | Medium | [LC 907](https://leetcode.com/problems/sum-of-subarray-minimums/) | Monotone stack, contribution of each element | - |
| 13 | Largest Rectangle in Histogram | Hard | [LC 84](https://leetcode.com/problems/largest-rectangle-in-histogram/) | Monotone stack for left/right boundaries | - |
| 14 | Maximum Width Ramp | Medium | [LC 962](https://leetcode.com/problems/maximum-width-ramp/) | Monotone stack for candidates | - |

### 15.4 DP + HashMap (Memoize by Complex State)
> **Core idea:** State space too large or non-sequential for arrays. `HashMap<state, value>`. Common: state=(index, set_of_choices).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 15 | Longest Arithmetic Subsequence | Medium | [LC 1027](https://leetcode.com/problems/longest-arithmetic-subsequence/) | dp[i][diff] via HashMap per index | - |
| 16 | Arithmetic Slices II | Hard | [LC 446](https://leetcode.com/problems/arithmetic-slices-ii-subsequence/) | dp[i][diff] = count of valid endings | - |
| 17 | Frog Jump | Hard | [LC 403](https://leetcode.com/problems/frog-jump/) | dp[stone][last_jump] via HashMap | - |

---

## 16. MATRIX EXPONENTIATION

### 16.1 Matrix Exponentiation — Linear Recurrence (Fast Power)
> **Core idea:** Express recurrence as matrix multiplication. Compute M^n in O(k³ log n). Use when n is huge (10^18).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Fibonacci (Large N) | Expert | [GFG](https://www.geeksforgeeks.org/matrix-exponentiation/) | M = [[1,1],[1,0]], M^n gives F(n) | - |
| 2 | Climbing Stairs (Large N) | Expert | [GFG](https://www.geeksforgeeks.org/matrix-exponentiation/) | Same Fibonacci matrix | - |
| 3 | Count Vowels Permutation (Fast) | Expert | [LC 1220](https://leetcode.com/problems/count-vowels-permutation/) | 5×5 transition matrix, raise to n-th power | DP O(n) |
| 4 | Student Attendance Record II (Fast) | Expert | [LC 552](https://leetcode.com/problems/student-attendance-record-ii/) | State matrix exponentiation | DP O(n) |
| 5 | Decode Ways Large N | Expert | [GFG](https://www.geeksforgeeks.org/count-possible-decodings-digit-sequence/) | 2×2 matrix for decode recurrence | DP |
| 6 | Domino Tiling Large N | Expert | [GFG](https://www.geeksforgeeks.org/tiling-problem/) | Matrix exp for tiling recurrence | DP |

---

## 17. MISCELLANEOUS ADVANCED DP

### 17.1 Divide and Conquer DP Optimization
> **Core idea:** When `dp[i][j]` satisfies monotone optimal split property (opt(i,j)≤opt(i,j+1)), reduce O(n²) transition to O(n log n) via D&C.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Divide Chocolate | Hard (Premium) | [LC 1231](https://leetcode.com/problems/divide-chocolate/) | Binary search + DP | - |
| 2 | Largest Sum of Averages | Medium | [LC 813](https://leetcode.com/problems/largest-sum-of-averages/) | D&C DP optimization | Naive O(kn²) |

### 17.2 Convex Hull Trick (CHT) / Li Chao Tree
> **Core idea:** Transition `dp[i] = min over j of (dp[j] + b[j]*a[i])` = linear function of a[i] for each j. CHT maintains lower envelope, reducing O(n²) to O(n log n) or O(n).

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 3 | Minimum Cost to Cut Sticks (CHT) | Hard | [LC 1547](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/) | Interval DP or CHT | Interval DP |
| 4 | Building Bridges | Hard | [GFG](https://www.geeksforgeeks.org/dynamic-programming-building-bridges/) | CHT on LIS-style DP | LIS |
| 5 | Sequence of Products | Expert | [GFG](https://www.geeksforgeeks.org/convex-hull-trick-and-lis/) | Classic CHT application | - |

### 17.3 SOS DP (Sum over Subsets)
> **Core idea:** `dp[mask]` = sum over all subsets of mask. Computed in O(n × 2^n) using inclusion principle per bit.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Sum over Subsets (SOS DP) | Expert | [GFG](https://www.geeksforgeeks.org/sum-subsets-dynamic-programming/) | dp[mask][i] += dp[mask^(1<<i)][i-1] | Brute O(3^n) |
| 7 | Count Pairs with XOR in Range | Hard | [GFG](https://www.geeksforgeeks.org/count-pairs-with-given-xor/) | SOS DP on trie | Trie |
| 8 | Maximum XOR of Two Numbers | Medium | [LC 421](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/) | Greedy trie / SOS | Trie |

### 17.4 Suffix/Prefix DP
> **Core idea:** `dp[i]` computed right-to-left. Optimal decision at i depends on best outcome from i+1 onward.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 9 | Stone Game VIII | Hard | [LC 1872](https://leetcode.com/problems/stone-game-viii/) | Suffix prefix sum DP, pick prefix | - |
| 10 | Minimum Cost to Make Array Equal | Hard | [LC 2448](https://leetcode.com/problems/minimum-cost-to-make-array-equal/) | Prefix/suffix cost + binary search | - |
| 11 | Longest Chunked Palindrome Decomposition | Hard | [LC 1147](https://leetcode.com/problems/longest-chunked-palindrome-decomposition/) | Two-pointer DP from both ends + hashing | Greedy |
| 12 | Number of Ways to Divide a Long Corridor | Hard | [LC 2147](https://leetcode.com/problems/number-of-ways-to-divide-a-long-corridor/) | Multiplication of gaps between seat pairs | - |

### 🆕 17.5 WQS Binary Search (Aliens Trick)
> **Core idea:** When a DP problem requires **exactly K operations** and the answer is a convex function of K, binary search on a penalty λ per operation. Adding this penalty converts "exactly K" into "any number, but each operation costs λ." The optimal number of operations at penalty λ is a non-increasing function of λ. Binary search on λ until optimal_count(λ) = K. Reduces O(nK) to O(n log(ValueRange)). Signal: "exactly K" partitions/groups/cuts with convex cost structure.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Aliens Trick Template | Expert | [GFG](https://www.geeksforgeeks.org/wqs-binary-search/) | Binary search on λ; for each λ solve unconstrained DP | - |
| 2 | Maximize Score After K Operations (CF) | Expert | [CF 739E](https://codeforces.com/problemset/problem/739/E) | Origin problem; λ per operation, binary search | - |
| 3 | Split Array with K Subarrays (Min Cost) | Expert | [GFG](https://www.geeksforgeeks.org/wqs-binary-search/) | Min cost of exactly K splits; convex in K | D&C DP |
| 4 | Minimum Cost to Hire K Workers | Hard | [LC 857](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/) | WQS applicable; binary search on wage ratio | Greedy+heap |
| 5 | K-Partition with Min Sum of Max | Hard | [GFG](https://www.geeksforgeeks.org/wqs-binary-search/) | Convex cost in K; WQS reduces to O(n log V) | Binary search |

### 🆕 17.6 Slope Trick
> **Core idea:** When the DP cost function is piecewise linear convex (a V-shape that shifts/extends), maintain the **slope sequence** using two priority queues (max-heap for left slopes, min-heap for right slopes) instead of storing dp[i] = scalar. Transitions correspond to inserting/removing breakpoints in O(log n). Reduces "make array non-decreasing with min cost" type problems from O(n²) to O(n log n). Signal: "minimum cost to make array monotone/sorted" where cost is sum of absolute differences.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Slope Trick Template | Expert | [GFG](https://www.geeksforgeeks.org/slope-trick-algorithm/) | Maintain two heaps for left/right slopes of convex function | Naive O(n²) |
| 2 | Min Cost to Make Array Non-Decreasing | Hard | [GFG](https://www.geeksforgeeks.org/slope-trick-algorithm/) | Classic slope trick; push, then fix heap tops | - |
| 3 | Min Possible Integer After K Adjacent Swaps | Hard | [LC 1505](https://leetcode.com/problems/minimum-possible-integer-after-at-most-k-adjacent-swaps-on-digits/) | Slope trick on positions; track cost of moving each digit | BIT |
| 4 | Make Array Non-Decreasing or Non-Increasing | Medium | [LC 2263](https://leetcode.com/problems/make-array-non-decreasing-or-non-increasing/) | Run slope trick twice (asc + desc), take min | - |
| 5 | Height Checker (Sorted vs Original) | Easy | [LC 1051](https://leetcode.com/problems/height-checker/) | Warm-up: count positions where sort disagrees | Counting sort |

### 🆕 17.7 Knuth's Optimization (Quadrangle Inequality for Interval DP)
> **Core idea:** When the cost function in interval DP satisfies the **quadrangle inequality** `cost(a,c)+cost(b,d) ≤ cost(a,d)+cost(b,c)` for a≤b≤c≤d, the optimal split point `opt[i][j]` is monotone: `opt[i][j-1] ≤ opt[i][j] ≤ opt[i+1][j]`. Reduces O(n³) interval DP to O(n²). Signal: interval DP where the cost function satisfies the "concave SMAWK" property — checking if cost is derived from sorted structure or prefix sums usually confirms it.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | Knuth's Optimization Template | Expert | [GFG](https://www.geeksforgeeks.org/knuths-optimization-in-dynamic-programming/) | Verify quadrangle inequality; add opt[i][j] tracking | O(n³) interval DP |
| 2 | Optimal BST (Knuth's) | Expert | [GFG](https://www.geeksforgeeks.org/optimal-binary-search-tree-dp-24/) | Classic Knuth application; cost satisfies QI | O(n³) |
| 3 | Minimum Cost to Merge Files | Expert | [GFG](https://www.geeksforgeeks.org/minimum-cost-to-merge-files/) | Merge cost satisfies QI; O(n²) via Knuth | O(n³) |
| 4 | Minimum Cost to Cut a Stick (Knuth's) | Hard | [LC 1547](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/) | Cut cost = length of stick; QI holds; O(n²) | O(n³), 5.1 |
| 5 | Optimal File Merge | Expert | [GFG](https://www.geeksforgeeks.org/knuths-optimization-in-dynamic-programming/) | File sizes → QI holds; apply Knuth | O(n³) |

---

## 🆕 18. MEET IN THE MIDDLE DP

### 18.1 MITM — Subset Sum Enumeration + Binary Search
> **Core idea:** Split n items into two halves of n/2 each. Enumerate all 2^(n/2) subset sums for each half independently. Sort one half's sums, then for each sum in the other half, binary search for the best complement. Reduces O(2^n) to O(2^(n/2) · log). Signal: n≤40 (too large for 2^n bitmask DP but too small for polynomial approach), target = "find subset with sum closest to X."

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 1 | MITM Template | Expert | [GFG](https://www.geeksforgeeks.org/meet-in-the-middle/) | Split into two halves; enumerate, sort, binary search | O(2^n) brute |
| 2 | Partition Array Min Sum Diff | Hard | [LC 2035](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/) | Split n/2 + n/2; match sorted halves via binary search | 0/1 Knapsack |
| 3 | Closest Subsequence Sum | Hard | [LC 1755](https://leetcode.com/problems/closest-subsequence-sum/) | All subset sums of two halves; binary search for closest to goal | - |
| 4 | Split Array with Same Average | Hard | [LC 805](https://leetcode.com/problems/split-array-with-same-average/) | MITM on subset sums + fraction check | - |
| 5 | Count Subsets with Sum in Range | Hard | [GFG](https://www.geeksforgeeks.org/meet-in-the-middle/) | Two halves enumerated; sorted + prefix count | - |

### 18.2 MITM — State Space Halving (Bidirectional BFS + DP)
> **Core idea:** Problem state space is too large to explore from one end. Explore from both ends, store reachable states at middle layer, then join. Common in word ladder variants, 2-player game states, circuit satisfiability.

| # | Problem | Difficulty | Link | Key Concept | Alternative |
|---|---------|------------|------|-------------|-------------|
| 6 | Word Ladder (Bidirectional BFS) | Hard | [LC 127](https://leetcode.com/problems/word-ladder/) | BFS from both source and target; meet at middle | Single BFS |
| 7 | Minimum XOR Sum of Two Arrays | Hard | [LC 1879](https://leetcode.com/problems/minimum-xor-sum-of-two-arrays/) | MITM applicable for large n variants | Bitmask DP |

---

## 19. DP PATTERNS MASTER REFERENCE

| Pattern | Core Mechanism | Time Complexity | Signal Words |
|---------|---------------|-----------------|--------------|
| **Fibonacci 1D** | dp[i] = f(dp[i-1], dp[i-2]) | O(n) | "ways to climb", "tilings" |
| **Kadane** | dp[i] = max(nums[i], dp[i-1]+nums[i]) | O(n) | "max subarray", "contiguous" |
| **House Robber** | dp[i] = max(dp[i-1], dp[i-2]+val[i]) | O(n) | "no adjacent", "skip or take" |
| **Decision DP** | dp[i] = max(take+dp[i+skip], dp[i+1]) | O(n) | "take or skip with penalty", "brainpower" |
| **0/1 Knapsack** | Backward iteration, each item once | O(n·W) | "subset", "partition", "0 or 1 of each" |
| **Unbounded Knapsack** | Forward iteration, reuse items | O(n·W) | "unlimited coins", "rod cutting" |
| **LCS** | dp[i][j] = match or skip | O(n·m) | "common subsequence", "edit distance" |
| **LIS O(n²)** | dp[i] = max(dp[j]+1) for j<i | O(n²) | "increasing subsequence" |
| **LIS O(n log n)** | Binary search on tails[] | O(n log n) | Same, larger n |
| **Edit Distance** | Insert/Delete/Replace at each cell | O(n·m) | "convert string", "operations" |
| **Wildcard/Regex** | 2D DP with special char handling | O(n·m) | "*, ?, ." pattern matching |
| **Palindrome Interval** | Fill by interval length, use borders | O(n²) | "palindromic subsequence/partition" |
| **Interval DP (MCM)** | dp[i][j] = opt over split k | O(n³) | "merge", "triangulation", "burst" |
| **Knuth's Opt** | Monotone split point; O(n²) interval DP | O(n²) | QI holds on cost function |
| **Multi-Pointer DP** | State = two independent boundary indices | O(n²) to O(n³) | "two agents", "shrinking (i,j) window" |
| **Minimax** | dp = score_diff, maximize for current player | O(n²) | "two players", "optimal play" |
| **Bitmask DP** | State = subset bitmask | O(2ⁿ · n) | "all nodes", "assign each to one" |
| **Digit DP** | Build digit by digit, track tight | O(digits · states) | "count numbers with property in [l,r]" |
| **Tree DP** | Post-order DFS, combine children | O(n) | "tree", "subtree", "path through node" |
| **Re-rooting** | Two-pass: bottom-up then top-down | O(n) | "answer for each node as root" |
| **State Machine** | Explicit states + transitions | O(n · states) | "attendance", "cooldown", "paint" |
| **Probability DP** | dp[state] = probability/expectation | O(states) | "probability", "expected value" |
| **Matrix Exp** | M^n via fast exponentiation | O(k³ log n) | "n is huge (10^18)", linear recurrence |
| **CHT / D&C Opt** | Lower envelope of linear functions | O(n log n) | dp[j] + b[j]*a[i] form |
| **WQS Binary Search** | Binary search on penalty λ; remove K constraint | O(n log V) | "exactly K operations", convex in K |
| **Slope Trick** | Maintain convex function via two heaps | O(n log n) | "min cost to make array monotone" |
| **SOS DP** | Sum over all subsets of a mask | O(n · 2ⁿ) | "sum over subsets", "AND/OR queries" |
| **Suffix DP** | dp[i] computed right-to-left | O(n) | "best from position i onward" |
| **DP + Binary Search** | Binary search for optimal previous state | O(n log n) | "non-overlapping intervals", LIS |
| **DP + Segment Tree** | Range query in transition | O(n log n) | "best in range [l..r] of dp values" |
| **Meet in the Middle** | Split into two n/2 halves, enumerate+join | O(2^(n/2) · log) | n≈40, "subset sum", "bidirectional" |
| **Rolling Hash + DP** | O(1) substring comparison enables standard DP | O(n log n) | "check if substring matches in O(1)" |

---

> **Legend:** LC = LeetCode | GFG = GeeksForGeeks | CF = Codeforces | Premium = paid subscription | 🆕 = added in v2
> **Tip:** If stuck: (1) What is my state? (2) What is my transition? (3) What is my base case? (4) What order to fill?
> **v2 New Sections:** 1.9 Decision DP · 3.14 Rolling Hash DP · 4.8 Multi-Pointer DP · 6.6 Assignment Partition · 17.5 WQS Binary Search · 17.6 Slope Trick · 17.7 Knuth's Optimization · 18 Meet in the Middle DP
