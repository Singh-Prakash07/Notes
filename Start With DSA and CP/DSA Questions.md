# 🎯 COMPLETE PROBLEM SHEET — Binary Search, Sliding Window, Two Pointers, and Beyond
> Master 20+ fundamental algorithms & techniques. ~250 Problems. LeetCode + GFG.
> **Excludes:** DP (separate sheet), Graph algorithms (separate sheet).
> **Includes:** Everything else you need to crack interviews.

---

## HOW TO READ THIS SHEET

- Each **subsection** = one **distinct technique/pattern**
- The `> Core idea:` block explains the mechanism before solving
- Problems in multiple categories appear in **primary** section; alternatives noted
- 🆕 marks additions from v1
- **Master Reference** at the end: quick lookup by topic

---

## 1. BINARY SEARCH

### 1.1 Classic Binary Search — Exact Match

> **Core idea:** Sorted array, divide in half, discard half with no target. O(log n).
> Precondition: array MUST be sorted.
> Template: `while lo <= hi`, update `lo = mid+1` or `hi = mid-1`.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Binary Search | Easy | [LC 704](https://leetcode.com/problems/binary-search/) | Classic: return mid if found, else -1 |
| 2 | First Bad Version | Easy | [LC 278](https://leetcode.com/problems/first-bad-version/) | Find first True in boolean array |
| 3 | Search Insert Position | Easy | [LC 35](https://leetcode.com/problems/search-for-a-position-of-an-element-in-a-sorted-array/) | Return insertion point if not found |
| 4 | Guess Number Higher or Lower | Easy | [LC 374](https://leetcode.com/problems/guess-number-higher-or-lower/) | Use API to binary search |

### 1.2 Boundary Search — Leftmost / Rightmost

> **Core idea:** Find **first** occurrence (leftmost) or **last** occurrence (rightmost) of target in sorted array with duplicates. O(log n).
> Template: `if nums[mid] >= target: hi = mid` for leftmost; `if nums[mid] <= target: lo = mid+1` for rightmost.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 5 | Find First and Last Position | Medium | [LC 34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) | Find both boundaries in O(log n) |
| 6 | First Occurrence of Target | Medium | [GFG](https://www.geeksforgeeks.org/find-first-and-last-positions-of-an-element-in-an-array/) | Leftmost binary search |
| 7 | Last Occurrence of Target | Medium | [GFG](https://www.geeksforgeeks.org/find-first-and-last-positions-of-an-element-in-an-array/) | Rightmost binary search |
| 8 | Count Occurrences of Element | Easy | [GFG](https://www.geeksforgeeks.org/count-number-of-occurrences-in-a-sorted-array/) | rightmost - leftmost + 1 |
| 9 | Missing Number in Sorted Array | Easy | [GFG](https://www.geeksforgeeks.org/find-the-missing-number-in-sorted-array/) | Expected vs actual position |

### 1.3 Rotated Sorted Array

> **Core idea:** Array is sorted but rotated at pivot. Still O(log n) — determine which half is sorted, search that if target is there, else search other half.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 10 | Search in Rotated Sorted Array | Medium | [LC 33](https://leetcode.com/problems/search-in-rotated-sorted-array/) | Determine sorted half, recurse on answer half |
| 11 | Search in Rotated Sorted Array II (Duplicates) | Medium | [LC 81](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) | Handle lo==mid==hi (collapse range) |
| 12 | Find Minimum in Rotated Sorted Array | Medium | [LC 153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) | Pivot location = minimum |
| 13 | Find Minimum in Rotated Sorted Array II | Medium | [LC 154](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/) | Duplicates make it tricky |
| 14 | Find Peak Element | Medium | [LC 162](https://leetcode.com/problems/find-peak-element/) | nums[mid] vs neighbors |

### 1.4 Binary Search on Answer

> **Core idea:** Not searching an array — instead, binary search on the **answer space**. For each candidate answer, check if it's feasible. O(log answer_range * feasibility_check_time).
> Pattern: `while lo < hi: mid = lo + (hi - lo) // 2; if feasible(mid): hi = mid else: lo = mid + 1`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 15 | Capacity to Ship Packages | Medium | [LC 1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) | Search on capacity; check feasibility in O(n) |
| 16 | Koko Eating Bananas | Medium | [LC 875](https://leetcode.com/problems/koko-eating-bananas/) | Search on eating speed |
| 17 | Minimum Number of Days to Make Bouquets | Medium | [LC 1482](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/) | Search on days |
| 18 | Binary Search on Floating Point (Square Root) | Medium | [LC 69](https://leetcode.com/problems/sqrtx/) | Search on [1, x]; check mid*mid <= x |
| 19 | Find Kth Smallest Pair Distance | Hard | [LC 719](https://leetcode.com/problems/find-the-kth-smallest-sum-in-a-matrix/) | Search on distance; count pairs <= distance |
| 20 | Minimise Maximum of Array | Medium | [LC 2439](https://leetcode.com/problems/minimize-the-maximum-difference-of-pair-sums-in-two-arrays/) | Search on max difference |
| 21 | Find Minimum Time to Complete All Tasks | Hard | [LC 1901](https://leetcode.com/problems/minimum-time-to-complete-all-tasks-with-priority-constraints/) | Search on total time |

### 1.5 Binary Search on 2D Array

> **Core idea:** Treat 2D as 1D (row-major flattening), binary search. Or row-wise binary search.
> Convert (index) ↔ (row, col): `row = index // cols; col = index % cols`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 22 | Search a 2D Matrix | Medium | [LC 74](https://leetcode.com/problems/search-a-2d-matrix/) | Treat as 1D flattened array |
| 23 | Search a 2D Matrix II | Medium | [LC 240](https://leetcode.com/problems/search-a-2d-matrix-ii/) | Start top-right, go left/down based on comparison |
| 24 | Find K-th Smallest in Sorted Matrix | Hard | [LC 378](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/) | Binary search on value; count elements <= mid |

### 1.6 Binary Search on Indices with Custom Condition

> **Core idea:** Array may not store the target directly. Instead, binary search on indices where a **predicate** becomes True.
> Example: Find first index where sum >= target.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 25 | Split Array Largest Sum | Hard | [LC 410](https://leetcode.com/problems/split-array-largest-sum/) | Search on max sum; check if k splits suffice |
| 26 | Painter's Partition | Hard | [GFG](https://www.geeksforgeeks.org/painters-partition-problem/) | Search on max paint; greedy check |
| 27 | Find the Kth Positive Missing Number | Medium | [LC 1539](https://leetcode.com/problems/find-the-kth-positive-missing-number/) | Offset: num[i] vs expected |
| 28 | Magnetic Force Between Two Balls | Medium | [LC 1552](https://leetcode.com/problems/magnetic-force-between-two-balls/) | Search on min distance; greedy placement |

---

## 2. TWO POINTERS

### 2.1 Opposite Ends — Left and Right

> **Core idea:** One pointer at start, one at end. Move inward based on condition. Exploits sorted/monotone property. O(n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Two Sum (Sorted Array) | Medium | [LC 167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) | If sum < target: lo++; else: hi-- |
| 2 | Container With Most Water | Medium | [LC 11](https://leetcode.com/problems/container-with-most-water/) | Move pointer at shorter height inward |
| 3 | Trapping Rain Water | Hard | [LC 42](https://leetcode.com/problems/trapping-rain-water/) | Maintain left-max and right-max pointers |
| 4 | 3Sum | Medium | [LC 15](https://leetcode.com/problems/3sum/) | Fix one element, two-pointer on rest; sort & skip duplicates |
| 5 | 3Sum Closest | Medium | [LC 16](https://leetcode.com/problems/3sum-closest/) | Track closest sum while moving pointers |
| 6 | 4Sum | Medium | [LC 18](https://leetcode.com/problems/4sum/) | Two nested loops, two-pointer for inner |
| 7 | Remove Duplicates II | Medium | [LC 80](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) | Pointer tracks position to write |
| 8 | Merge Sorted Arrays | Easy | [LC 88](https://leetcode.com/problems/merge-sorted-array/) | Merge in-place from back |

### 2.2 Fast and Slow (Floyd's Cycle Detection)

> **Core idea:** Two pointers at different speeds. Slow moves 1 step, fast moves 2 steps. If they meet, there is a cycle. O(n) space-optimal cycle detection.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 9 | Linked List Cycle | Easy | [LC 141](https://leetcode.com/problems/linked-list-cycle/) | Pointers meet iff cycle exists |
| 10 | Linked List Cycle II | Medium | [LC 142](https://leetcode.com/problems/linked-list-cycle-ii/) | After meeting, move to start; meet again at cycle start |
| 11 | Happy Number | Easy | [LC 202](https://leetcode.com/problems/happy-number/) | Detect cycle in number transformation |
| 12 | Middle of Linked List | Easy | [LC 876](https://leetcode.com/problems/middle-of-the-linked-list/) | When fast reaches end, slow is at middle |
| 13 | Palindrome Linked List | Easy | [LC 234](https://leetcode.com/problems/palindrome-linked-list/) | Find middle, reverse second half, compare |

### 2.3 Same Direction — Sliding/Fast Catch-Up

> **Core idea:** Both pointers move in same direction, but at different speeds or with different logic. Used for removing elements, in-place modifications. O(n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 14 | Remove Element | Easy | [LC 27](https://leetcode.com/problems/remove-element/) | j tracks write position, i scans |
| 15 | Remove Duplicates from Sorted Array | Easy | [LC 26](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) | j is write position for unique elements |
| 16 | Move Zeroes | Easy | [LC 283](https://leetcode.com/problems/move-zeroes/) | i scans, j marks position for non-zero |
| 17 | Reverse String | Easy | [LC 344](https://leetcode.com/problems/reverse-string/) | Swap ends, move inward |
| 18 | Valid Palindrome | Easy | [LC 125](https://leetcode.com/problems/valid-palindrome/) | Skip non-alphanumeric, compare |
| 19 | Sort Array by Parity | Easy | [LC 905](https://leetcode.com/problems/sort-array-by-parity/) | Even on left, odd on right |
| 20 | Backspace String Compare | Easy | [LC 844](https://leetcode.com/problems/backspace-string-compare/) | Two pointers from end, skip backspaces |

### 2.4 Multiple Pointers (Three or More)

> **Core idea:** Track more than two positions simultaneously. E.g., three pointers for array partitioning, or for tracking multiple moving objects.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 21 | Sort Array by Color (Dutch National Flag) | Medium | [GFG](https://www.geeksforgeeks.org/segregate-0s-and-1s-in-an-array/) | Three pointers: low, mid, high; partition in place |
| 22 | Trapping Rain Water II (2D) | Hard | [LC 407](https://leetcode.com/problems/trapping-rain-water-ii/) | Priority queue with multiple boundaries |

---

## 3. SLIDING WINDOW

### 3.1 Fixed Size Window

> **Core idea:** Window of fixed size k slides over array. Compute answer for each window position. O(n) using deque or suffix optimization.
> Pattern: Add new element right, remove old element left when window is full.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Maximum Sum Subarray of Size K | Easy | [GFG](https://www.geeksforgeeks.org/find-maximum-sum-of-a-subarray-of-size-k/) | Compute sum(nums[0..k-1]), slide |
| 2 | Grumpy Bookstore Owner | Medium | [LC 1052](https://leetcode.com/problems/grumpy-bookstore-owner/) | Fixed window of k minutes; maximize satisfied customers |
| 3 | Sliding Window Maximum | Hard | [LC 239](https://leetcode.com/problems/sliding-window-maximum/) | Monotonic deque: O(n) max per window |
| 4 | Sliding Window Median | Hard | [LC 295](https://leetcode.com/problems/find-median-from-data-stream/) | Two heaps track window median |
| 5 | Repeated DNA Sequence | Medium | [LC 187](https://leetcode.com/problems/repeated-dna-sequences/) | Rolling hash or HashMap, find all 10-length repeats |
| 6 | Max Consecutive Ones III | Medium | [LC 1004](https://leetcode.com/problems/max-consecutive-ones-iii/) | Window with at most K zeros; maximize length |
| 7 | Number of Subarrays with Bounded Maximum | Medium | [LC 795](https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/) | Count subarrays with max in [L, R] |

### 3.2 Variable Size Window — Expand-Shrink Pattern

> **Core idea:** Window expands by moving right. When condition violated (e.g., sum > target), shrink from left until valid. O(n).
> Pattern: `while condition_violated: left += 1`. Works on monotone properties.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 8 | Minimum Window Substring | Hard | [LC 76](https://leetcode.com/problems/minimum-window-substring/) | Expand right, shrink left when valid |
| 9 | Longest Substring Without Repeating Characters | Medium | [LC 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | HashMap tracks last index; shrink when duplicate |
| 10 | Longest Substring with At Most Two Distinct | Medium | [LC 159](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/) | HashMap freq; shrink when distinct > 2 |
| 11 | Longest Repeating Character Replacement | Medium | [LC 424](https://leetcode.com/problems/longest-repeating-character-replacement/) | Can replace at most k chars; expand/shrink |
| 12 | Max Consecutive Ones III | Medium | [LC 1004](https://leetcode.com/problems/max-consecutive-ones-iii/) | Subarray with at most k zeros |
| 13 | Minimum Size Subarray Sum | Medium | [LC 209](https://leetcode.com/problems/minimum-size-subarray-sum/) | Sum >= target; minimize length |
| 14 | Fruit Into Baskets | Medium | [LC 904](https://leetcode.com/problems/fruit-into-baskets/) | At most 2 types; maximize consecutive |
| 15 | Subarrays with K Different Integers | Hard | [LC 992](https://leetcode.com/problems/subarrays-with-k-different-integers/) | atMostK(k) - atMostK(k-1) |

### 3.3 Sliding Window with Frequency / HashMap

> **Core idea:** Track character/element frequencies in window using HashMap. Common: finding anagrams, permutations, substrings matching a pattern.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 16 | Permutation in String | Medium | [LC 567](https://leetcode.com/problems/permutation-in-string/) | Check if s2 contains permutation of s1 |
| 17 | Find All Anagrams in String | Medium | [LC 438](https://leetcode.com/problems/find-all-anagrams-in-a-string/) | All windows of size len(p) that are anagrams of p |
| 18 | Find the Celebrity | Medium | [LC 277](https://leetcode.com/problems/find-the-celebrity/) | Pair-wise comparison; find person known by all |
| 19 | Substring with Concatenation of All Words | Hard | [LC 30](https://leetcode.com/problems/substring-with-concatenation-of-all-words/) | Window of fixed words length; match all words |
| 20 | Longest Substring with Distinct Characters | Medium | [GFG](https://www.geeksforgeeks.org/longest-substring-without-repeating-characters/) | HashMap + two pointers |

### 3.4 Monotonic Deque (Sliding Window Min/Max)

> **Core idea:** Deque stores indices (or values) in monotonic order. Efficient O(n) computation of min/max over all windows. Remove stale/dominated elements.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 21 | Sliding Window Maximum (with Deque) | Hard | [LC 239](https://leetcode.com/problems/sliding-window-maximum/) | Deque stores indices in decreasing value order |
| 22 | Sliding Window Minimum | Medium | [GFG](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/) | Deque in increasing order |
| 23 | Jump Game VI | Medium | [LC 1696](https://leetcode.com/problems/jump-game-vi/) | Deque maintains max dp[i] in window [i-k, i] |
| 24 | Constrained Subsequence Sum | Hard | [LC 1425](https://leetcode.com/problems/constrained-subsequence-sum/) | dp[i] + max(dp window); deque for window max |

---

## 4. PREFIX SUM

### 4.1 1D Prefix Sum

> **Core idea:** Precompute cumulative sums. Query sum(l, r) in O(1) instead of O(r-l).
> `prefix[i] = sum(nums[0..i-1]); sum(l, r) = prefix[r+1] - prefix[l]`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Prefix Sum (Template) | Easy | [GFG](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-in-competitive-programming/) | Build prefix array, O(1) range query |
| 2 | Running Sum of 1D Array | Easy | [LC 1480](https://leetcode.com/problems/running-sum-of-1d-array/) | Output cumulative sums |
| 3 | Range Sum Query | Medium | [LC 303](https://leetcode.com/problems/range-sum-query-immutable/) | Immutable array, O(1) range queries |
| 4 | Continuous Subarray Sum | Medium | [LC 523](https://leetcode.com/problems/continuous-subarray-sum/) | Find subarray sum divisible by k (modular arithmetic) |
| 5 | Subarray Sum Equals K | Medium | [LC 560](https://leetcode.com/problems/subarray-sum-equals-k/) | HashMap of prefix sums; count prefix[j] = prefix[i] - k |
| 6 | Contiguous Array | Medium | [LC 525](https://leetcode.com/problems/contiguous-array/) | Treat 0 as -1; find subarray sum = 0 |

### 4.2 2D Prefix Sum

> **Core idea:** 2D cumulative sum. Query rect sum in O(1).
> `prefix[i][j] = sum of all elements in rect (0,0) to (i-1,j-1)`
> Rect sum (r1,c1) to (r2,c2) = `prefix[r2+1][c2+1] - prefix[r1][c2+1] - prefix[r2+1][c1] + prefix[r1][c1]`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 7 | 2D Range Sum Query | Medium | [LC 304](https://leetcode.com/problems/range-sum-query-2d-immutable/) | 2D prefix sum, O(1) rect queries |
| 8 | Number of Submatrices with All Ones | Medium | [LC 2906](https://leetcode.com/problems/count-sub-matrices-with-all-ones/) | 2D prefix or histogram height tracking |
| 9 | Max Sum of Rectangle No Larger Than K | Hard | [LC 363](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/) | Collapse columns; solve 1D with sorted set |

### 4.3 Prefix XOR

> **Core idea:** Prefix XOR: `xor[i] = xor[0..i-1]`. Range XOR: `xor(l, r) = prefix[r+1] ^ prefix[l]`.
> XOR is its own inverse: `a ^ a = 0`.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 10 | XOR Queries of a Subarray | Medium | [LC 1310](https://leetcode.com/problems/xor-queries-of-a-subarray/) | Prefix XOR for O(1) range XOR |
| 11 | Find Array Given Subset Sums | Hard | [LC 1982](https://leetcode.com/problems/find-array-given-subset-sums/) | Use XOR properties |

### 4.4 Prefix Sum with HashMap

> **Core idea:** Store prefix sums in HashMap with their first occurrence index. Find subarrays with a specific sum property in O(n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 12 | Subarray Sum Equals K | Medium | [LC 560](https://leetcode.com/problems/subarray-sum-equals-k/) | HashMap[prefix] = count; find prefix - k |
| 13 | Contiguous Array (0s and 1s) | Medium | [LC 525](https://leetcode.com/problems/contiguous-array/) | Treat 0→-1; find sum = 0 |
| 14 | Maximum Size Subarray Sum Equals K | Medium | [LC 325](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/) | Longest subarray with sum = k |
| 15 | Find Pivot Index | Easy | [LC 724](https://leetcode.com/problems/find-pivot-index/) | left_sum == right_sum at index |

---

## 5. HASHING & HASHMAP

### 5.1 Frequency Counting

> **Core idea:** Count occurrences of elements. HashMap[element] = count. Used for finding majorities, duplicates, anagrams.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Majority Element | Easy | [LC 169](https://leetcode.com/problems/majority-element/) | Element with count > n/2 |
| 2 | Majority Element II | Medium | [LC 229](https://leetcode.com/problems/majority-element-ii/) | All elements with count > n/3 |
| 3 | Contains Duplicate | Easy | [LC 217](https://leetcode.com/problems/contains-duplicate/) | Any duplicate exists? |
| 4 | Contains Duplicate II | Easy | [LC 219](https://leetcode.com/problems/contains-duplicate-ii/) | Duplicate within distance k |
| 5 | Valid Anagram | Easy | [LC 242](https://leetcode.com/problems/valid-anagram/) | Same frequencies |
| 6 | Group Anagrams | Medium | [LC 49](https://leetcode.com/problems/group-anagrams/) | Hash by sorted word or frequency |
| 7 | Intersection of Two Arrays | Easy | [LC 349](https://leetcode.com/problems/intersection-of-two-arrays/) | Common elements |
| 8 | Happy Number | Easy | [LC 202](https://leetcode.com/problems/happy-number/) | Detect cycle in digit sum transformations |
| 9 | First Unique Character | Easy | [LC 387](https://leetcode.com/problems/first-unique-character-in-a-string/) | First char with count = 1 |
| 10 | Ransom Note | Easy | [LC 383](https://leetcode.com/problems/ransom-note/) | Can we spell note with magazine letters? |

### 5.2 Index Tracking with HashMap

> **Core idea:** Store element → index mapping. Find pairs/relationships based on index constraints.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 11 | Two Sum | Easy | [LC 1](https://leetcode.com/problems/two-sum/) | HashMap[target - nums[i]] = index |
| 12 | Two Sum II | Medium | [LC 167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) | Sorted array: two pointers |
| 13 | Two Sum III | Easy | [LC 170](https://leetcode.com/problems/two-sum-iii-data-structure-design/) | Add/Find operations |
| 14 | Sum of Unique Elements | Easy | [LC 1748](https://leetcode.com/problems/sum-of-unique-elements/) | Sum elements with count = 1 |

### 5.3 Rolling Hash / Rabin-Karp

> **Core idea:** Hash substrings efficiently. Update hash in O(1) as window slides. Detect substring matches, find duplicates.
> `hash(s[i..j]) = (hash(s[i..j-1]) * base - s[i]*base^len + s[j]) % MOD`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 15 | Repeated DNA Sequence | Medium | [LC 187](https://leetcode.com/problems/repeated-dna-sequences/) | Rolling hash for all 10-length substrings |
| 16 | Longest Duplicate Substring | Hard (Premium) | [LC 1044](https://leetcode.com/problems/longest-duplicate-substring/) | Binary search + rolling hash |
| 17 | Search Pattern in Text (Rabin-Karp) | Medium | [GFG](https://www.geeksforgeeks.org/rabin-karp-algorithm-for-pattern-searching/) | Find pattern in text using hash |

### 5.4 Custom Hash Functions

> **Core idea:** Design hash for specific object types. Example: coordinate (r,c) → string "r,c" or tuple (r,c).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|=========|--------|-------------|
| 18 | Number of Islands | Medium | [LC 200](https://leetcode.com/problems/number-of-islands/) | BFS/DFS with visited set |
| 19 | LRU Cache | Medium | [LC 146](https://leetcode.com/problems/lru-cache/) | HashMap + Doubly Linked List |
| 20 | LFU Cache | Hard | [LC 460](https://leetcode.com/problems/lfu-cache/) | HashMap tracking freq, another HashMap per freq level |

---

## 6. SORTING

### 6.1 Comparison-Based Sorting

> **Core idea:** Merge Sort O(n log n), Quick Sort O(n log n) avg, Heap Sort O(n log n).
> Comparison sorts cannot do better than O(n log n) in worst case (information-theoretic lower bound).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Sort Array by Increasing Frequency | Easy | [LC 1636](https://leetcode.com/problems/sort-array-by-increasing-frequency/) | Custom comparator |
| 2 | Sort Integers by Number of Bits | Easy | [LC 1356](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/) | Bit count as sort key |
| 3 | Sort Array | Medium | [LC 912](https://leetcode.com/problems/sort-an-array/) | Implement or use built-in |
| 4 | Merge K Sorted Lists | Hard | [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/) | Min heap for K pointers |
| 5 | Merge Sorted Array | Easy | [LC 88](https://leetcode.com/problems/merge-sorted-array/) | Two pointers from back |

### 6.2 Counting Sort / Radix Sort

> **Core idea:** Count frequencies of each value (if range is small). O(n + k) where k = range. Or radix sort: sort by digits. O(d * (n + k)).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Sort Colors | Medium | [LC 75](https://leetcode.com/problems/sort-colors/) | Three colors (0, 1, 2); Dutch flag partition |
| 7 | Sort Integers II | Medium | [GFG](https://www.geeksforgeeks.org/counting-sort/) | Counting sort when range is O(n) |
| 8 | Maximum Gap | Hard | [LC 164](https://leetcode.com/problems/maximum-gap/) | Radix or bucket sort |
| 9 | Largest Number | Medium | [LC 179](https://leetcode.com/problems/largest-number/) | Custom comparator: a+b vs b+a |

### 6.3 Sort + Two Pointers / Greedy

> **Core idea:** Sort first to enable greedy or two-pointer logic.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 10 | Interval Scheduling | Medium | [LC 435](https://leetcode.com/problems/non-overlapping-intervals/) | Sort by end time, greedy |
| 11 | Two Sum (with array) | Easy | [LC 1](https://leetcode.com/problems/two-sum/) | Unsorted: HashMap; sorted: two pointers |
| 12 | 3Sum | Medium | [LC 15](https://leetcode.com/problems/3sum/) | Sort, fix one, two pointers |

### 6.4 Bucket Sort

> **Core idea:** Distribute elements into buckets, sort within each. O(n + k) if uniform distribution.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 13 | Maximum Gap | Hard | [LC 164](https://leetcode.com/problems/maximum-gap/) | Bucket sort for O(n) sort |

---

## 7. STACK

### 7.1 Basic Stack Operations

> **Core idea:** LIFO (Last In First Out). Push/pop in O(1). Used for matching, parsing, simulation.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Valid Parentheses | Easy | [LC 20](https://leetcode.com/problems/valid-parentheses/) | Push open; pop and match close |
| 2 | Minimum Stack | Medium | [LC 155](https://leetcode.com/problems/min-stack/) | Maintain min alongside stack |
| 3 | Simplify Path | Medium | [LC 71](https://leetcode.com/problems/simplify-path/) | Stack of directory names |
| 4 | Basic Calculator | Hard | [LC 224](https://leetcode.com/problems/basic-calculator/) | Parse expression with +, -, (, ) |
| 5 | Decode String | Medium | [LC 394](https://leetcode.com/problems/decode-string/) | Stack for nested structures like 2[a3[b]] |

### 7.2 Monotonic Stack (Next Greater/Smaller)

> **Core idea:** Stack keeps indices in monotonic order (decreasing or increasing). For each new element, pop elements that violate monotonicity — they just found their "next" element.
> Pattern: `while stack and nums[stack[-1]] < nums[i]: ... pop() ...`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Next Greater Element I | Easy | [LC 496](https://leetcode.com/problems/next-greater-element-i/) | Monotonic decreasing stack |
| 7 | Next Greater Element II (Circular) | Medium | [LC 503](https://leetcode.com/problems/next-greater-element-ii/) | Iterate twice |
| 8 | Next Smaller Element | Easy | [GFG](https://www.geeksforgeeks.org/next-smaller-element/) | Monotonic increasing stack |
| 9 | Daily Temperatures | Medium | [LC 739](https://leetcode.com/problems/daily-temperatures/) | Days until warmer (next greater) |
| 10 | Largest Rectangle in Histogram | Hard | [LC 84](https://leetcode.com/problems/largest-rectangle-in-histogram/) | Monotonic stack; pop finds left & right boundaries |
| 11 | Trapping Rain Water | Hard | [LC 42](https://leetcode.com/problems/trapping-rain-water/) | Monotonic decreasing stack tracks bars |
| 12 | Verify Preorder Serialization | Medium | [LC 331](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/) | Slots: start with 1, each node uses 1 and adds 2 |
| 13 | Remove K Digits | Medium | [LC 402](https://leetcode.com/problems/remove-k-digits-to-make-smallest-number/) | Monotonic increasing stack; remove to make small |
| 14 | Remove Duplicate Letters | Hard | [LC 316](https://leetcode.com/problems/remove-duplicate-letters/) | Monotonic stack + frequency tracking |
| 15 | Online Stock Span | Medium | [LC 901](https://leetcode.com/problems/online-stock-span/) | Monotonic stack tracks span (days of non-decreasing) |

### 7.3 Stack for Parsing / Matching

> **Core idea:** Parentheses, HTML tags, mathematical expressions — use stack to match and validate.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 16 | Valid Parentheses | Easy | [LC 20](https://leetcode.com/problems/valid-parentheses/) | Classic matching |
| 17 | Longest Valid Parentheses | Hard | [LC 32](https://leetcode.com/problems/longest-valid-parentheses/) | Stack tracks indices; pop gives matching length |
| 18 | Basic Calculator II | Medium | [LC 227](https://leetcode.com/problems/basic-calculator-ii/) | Handle +, -, *, / (*, / higher precedence) |

---
## 8. QUEUE & DEQUE

### 8.1 Basic Queue Operations

> **Core idea:** First-In-First-Out (FIFO) logic. Often used for BFS or maintaining a processing order.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Implement Queue using Stacks | Easy | [LC 232](https://leetcode.com/problems/implement-queue-using-stacks/) | Two stacks to simulate FIFO |
| 2 | Implement Stack using Queues | Easy | [LC 225](https://leetcode.com/problems/implement-stack-using-queues/) | Rotate queue to simulate LIFO |
| 3 | Number of Recent Calls | Easy | [LC 933](https://leetcode.com/problems/number-of-recent-calls/) | Queue to maintain a rolling time window |

### 8.2 Monotonic Queue

> **Core idea:** A queue whose elements are strictly increasing or decreasing. Used to find next/previous greater/smaller elements dynamically.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Daily Temperatures | Medium | [LC 739](https://leetcode.com/problems/daily-temperatures/) | Decreasing stack/queue for next greater |
| 5 | Shortest Subarray with Sum at Least K | Hard | [LC 862](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/) | Monotonic queue + prefix sum |

### 8.3 Deque (Double-Ended Queue)

> **Core idea:** $O(1)$ insertions and deletions at both ends. Perfect for sliding window maximum/minimum queries.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Sliding Window Maximum | Hard | [LC 239](https://leetcode.com/problems/sliding-window-maximum/) | Deque stores indices, maintain monotonic decreasing |
| 7 | Jump Game VI | Medium | [LC 1696](https://leetcode.com/problems/jump-game-vi/) | DP + Deque to find max in window |
| 8 | Design Circular Deque | Medium | [LC 641](https://leetcode.com/problems/design-circular-deque/) | Array/Node implementation of Deque |

---

## 9. HEAP / PRIORITY QUEUE

### 9.1 Top-K Elements

> **Core idea:** Maintain a min-heap of size K for "Top K Largest" or a max-heap of size K for "Top K Smallest". $O(n \log k)$.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Kth Largest Element in an Array | Medium | [LC 215](https://leetcode.com/problems/kth-largest-element-in-an-array/) | Min-heap of size K |
| 2 | Top K Frequent Elements | Medium | [LC 347](https://leetcode.com/problems/top-k-frequent-elements/) | Map frequencies, then min-heap |
| 3 | K Closest Points to Origin | Medium | [LC 973](https://leetcode.com/problems/k-closest-points-to-origin/) | Max-heap of size K based on distance |

### 9.2 Two Heaps

> **Core idea:** Use a max-heap for the lower half and a min-heap for the upper half to dynamically track the median.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Find Median from Data Stream | Hard | [LC 295](https://leetcode.com/problems/find-median-from-data-stream/) | Balance sizes of Max-Heap and Min-Heap |
| 5 | Sliding Window Median | Hard | [LC 480](https://leetcode.com/problems/sliding-window-median/) | Two heaps + lazy deletion of outgoing elements |

### 9.3 Merge Sequences

> **Core idea:** Push the start of each sequence into a min-heap. Pop the smallest, push the next element from that sequence.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Merge K Sorted Lists | Hard | [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/) | Min-heap tracks the head of each list |
| 7 | Find K Pairs with Smallest Sums | Medium | [LC 373](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/) | Min-heap tracks sum and indices `(i, j)` |

---

## 10. BIT MANIPULATION

### 10.1 Basic Bitwise Operations

> **Core idea:** Use AND `&`, OR `|`, NOT `~`, and Shifts `<<`, `>>` for $O(1)$ space and $O(1)$ time bit-level logic.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Number of 1 Bits | Easy | [LC 191](https://leetcode.com/problems/number-of-1-bits/) | `n & (n - 1)` removes the lowest set bit |
| 2 | Counting Bits | Easy | [LC 338](https://leetcode.com/problems/counting-bits/) | DP + bit logic: `dp[i] = dp[i >> 1] + (i & 1)` |
| 3 | Reverse Bits | Easy | [LC 190](https://leetcode.com/problems/reverse-bits/) | Bit shift and mask 32 times |

### 10.2 XOR Properties

> **Core idea:** `A ^ A = 0`, `A ^ 0 = A`. Order doesn't matter. Perfect for finding pairs/missing elements.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Single Number | Easy | [LC 136](https://leetcode.com/problems/single-number/) | XOR all elements, pairs cancel out |
| 5 | Missing Number | Easy | [LC 268](https://leetcode.com/problems/missing-number/) | XOR indices and array values |
| 6 | Single Number II | Medium | [LC 137](https://leetcode.com/problems/single-number-ii/) | Count bits at each position modulo 3 |

---

## 11. GREEDY ALGORITHMS

### 11.1 Array Greedy

> **Core idea:** Make the locally optimal choice at each step without looking back. Usually relies on sorting or tracking running max/min.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Maximum Subarray | Medium | [LC 53](https://leetcode.com/problems/maximum-subarray/) | Kadane's Algorithm: reset negative running sums |
| 2 | Jump Game | Medium | [LC 55](https://leetcode.com/problems/jump-game/) | Track the furthest reachable index |
| 3 | Jump Game II | Medium | [LC 45](https://leetcode.com/problems/jump-game-ii/) | Track current jump range and next max reach |

### 11.2 Logic / Allocation

> **Core idea:** Greedily fulfill constraints in a specific order (e.g., largest first, smallest first).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Gas Station | Medium | [LC 134](https://leetcode.com/problems/gas-station/) | If total gas >= cost, unique solution exists. Track running deficit. |
| 5 | Task Scheduler | Medium | [LC 621](https://leetcode.com/problems/task-scheduler/) | Schedule most frequent tasks first (math/greedy) |

---

## 12. BACKTRACKING

### 12.1 Subsets & Combinations

> **Core idea:** Explore all paths recursively. Decide whether to "include" or "skip" the current element. Time is usually $O(2^n)$.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Subsets | Medium | [LC 78](https://leetcode.com/problems/subsets/) | Standard include/exclude recursion |
| 2 | Subsets II | Medium | [LC 90](https://leetcode.com/problems/subsets-ii/) | Sort array, skip adjacent duplicates in loop |
| 3 | Combination Sum | Medium | [LC 39](https://leetcode.com/problems/combination-sum/) | Allow reusing the same element in recursion |

### 12.2 Permutations

> **Core idea:** Order matters. Time is $O(n!)$. Track used elements via boolean array, bitmask, or swapping elements in-place.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Permutations | Medium | [LC 46](https://leetcode.com/problems/permutations/) | Swap current index with recursive indices |
| 5 | Permutations II | Medium | [LC 47](https://leetcode.com/problems/permutations-ii/) | Sort + use a visited array to skip duplicates |

### 12.3 Grid Backtracking

> **Core idea:** Backtrack on a 2D matrix. Temporarily mark cells as visited, recurse, then unmark.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Word Search | Medium | [LC 79](https://leetcode.com/problems/word-search/) | DFS + marking grid cells as `#` |
| 7 | N-Queens | Hard | [LC 51](https://leetcode.com/problems/n-queens/) | Track attacked columns and diagonals (r+c, r-c) |

---

## 13. DIVIDE & CONQUER

### 13.1 Partitioning & Quick Select

> **Core idea:** Pick a pivot, partition the array, recurse on the relevant half. Average $O(n)$, worst $O(n^2)$.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Kth Largest Element in an Array | Medium | [LC 215](https://leetcode.com/problems/kth-largest-element-in-an-array/) | Quickselect (Hoare/Lomuto partition) |
| 2 | Sort an Array | Medium | [LC 912](https://leetcode.com/problems/sort-an-array/) | Implement standard Quicksort |

### 13.2 Merge Sort Applications

> **Core idea:** Divide into halves, solve independently, and merge logic often solves counting/inversion problems. $O(n \log n)$.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 3 | Sort an Array | Medium | [LC 912](https://leetcode.com/problems/sort-an-array/) | Implement standard Merge Sort |
| 4 | Count of Smaller Numbers After Self | Hard | [LC 315](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) | Count inversions during the merge step |

---

## 14. STRING ALGORITHMS (KMP, Z-Algorithm)

### 14.1 String Matching

> **Core idea:** Find a pattern of length `m` in a string of length `n` in $O(n+m)$ time without fallback.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Find Index of First Occurrence | Easy | [LC 28](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/) | Implement KMP (LPS array) or Rabin-Karp |
| 2 | Shortest Palindrome | Hard | [LC 214](https://leetcode.com/problems/shortest-palindrome/) | KMP LPS array on `S + "#" + reverse(S)` |

### 14.2 Structural Strings

> **Core idea:** Anagrams, character frequencies, and specific string formatting.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 3 | Valid Anagram | Easy | [LC 242](https://leetcode.com/problems/valid-anagram/) | Character frequency array of size 26 |
| 4 | Group Anagrams | Medium | [LC 49](https://leetcode.com/problems/group-anagrams/) | Use sorted string or freq tuple as hashmap key |

---

## 15. MATH & GEOMETRY

### 15.1 Math Basics

> **Core idea:** Modulo arithmetic, GCD, prime factorization, and fast exponentiation.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Pow(x, n) | Medium | [LC 50](https://leetcode.com/problems/powx-n/) | Binary exponentiation. $O(\log n)$ |
| 2 | Count Primes | Medium | [LC 204](https://leetcode.com/problems/count-primes/) | Sieve of Eratosthenes |
| 3 | Reverse Integer | Medium | [LC 7](https://leetcode.com/problems/reverse-integer/) | Pop and push digits via modulo 10 |

### 15.2 Geometry

> **Core idea:** Tracking coordinates, slopes, areas, and intersections on a 2D plane.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Max Points on a Line | Hard | [LC 149](https://leetcode.com/problems/max-points-on-a-line/) | Group points by simplified slope $\Delta y / \Delta x$ |
| 5 | Rectangle Area | Medium | [LC 223](https://leetcode.com/problems/rectangle-area/) | `Area1 + Area2 - Overlap Area` |

## 16. LINKED LIST

### 16.1 Basic Operations

> **Core idea:** Node with value and next pointer. Insert/delete at specific position.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Reverse Linked List | Easy | [LC 206](https://leetcode.com/problems/reverse-a-linked-list/) | Three pointers or recursion |
| 2 | Reverse Linked List II (Reverse Between) | Medium | [LC 92](https://leetcode.com/problems/reverse-linked-list-ii/) | Partial reversal |
| 3 | Palindrome Linked List | Easy | [LC 234](https://leetcode.com/problems/palindrome-linked-list/) | Find middle, reverse, compare |
| 4 | Remove Nth Node From End | Medium | [LC 19](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) | Two pointers k apart |
| 5 | Merge Two Sorted Lists | Easy | [LC 21](https://leetcode.com/problems/merge-two-sorted-lists/) | Compare and merge |

### 16.2 Cycle Detection

> **Core idea:** Floyd's cycle detection: slow and fast pointers meet iff cycle. Then reset one to start; they meet at cycle entry.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Linked List Cycle | Easy | [LC 141](https://leetcode.com/problems/linked-list-cycle/) | Slow/fast meet iff cycle |
| 7 | Linked List Cycle II | Medium | [LC 142](https://leetcode.com/problems/linked-list-cycle-ii/) | Reset to start after meeting |

### 16.3 Merge / Sort Linked Lists

> **Core idea:** Merge sorted lists or sort a list. Merge O(n + m), sort O(n log n) with merge sort.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 8 | Merge K Sorted Lists | Hard | [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/) | Min-heap of K heads |
| 9 | Sort List | Medium | [LC 148](https://leetcode.com/problems/sort-list/) | Merge sort on linked list |

### 16.4 Other Linked List Problems

> **Core idea:** Pointer manipulation, traversal, structural changes.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 10 | Intersection of Two Linked Lists | Easy | [LC 160](https://leetcode.com/problems/intersection-of-two-linked-lists/) | Two pointers, traverse both |
| 11 | LRU Cache | Medium | [LC 146](https://leetcode.com/problems/lru-cache/) | HashMap + Doubly Linked List |
| 12 | LFU Cache | Hard | [LC 460](https://leetcode.com/problems/lfu-cache/) | HashMap + frequency tracking |

---

## 17. TREES (BFS/DFS, BST, Traversals)

### 17.1 BFS — Level Order Traversal

> **Core idea:** Queue-based traversal. Visit nodes level by level. O(n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Level Order Traversal | Medium | [LC 102](https://leetcode.com/problems/binary-tree-level-order-traversal/) | Queue per level |
| 2 | Level Order II (Bottom-Up) | Easy | [LC 107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/) | Reverse result |
| 3 | Zigzag Level Order | Medium | [LC 103](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) | Alternate direction per level |
| 4 | Average of Levels | Easy | [LC 637](https://leetcode.com/problems/average-of-levels-in-binary-tree/) | Track sum/count per level |
| 5 | Right View of Tree | Medium | [LC 199](https://leetcode.com/problems/binary-tree-right-side-view/) | Last node of each level |

### 17.2 DFS — Pre/In/Post Order

> **Core idea:** Recursive traversal. Pre-order (node, left, right), in-order (left, node, right), post-order (left, right, node). O(n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Inorder Traversal | Easy | [LC 94](https://leetcode.com/problems/binary-tree-inorder-traversal/) | Left, node, right |
| 7 | Preorder Traversal | Easy | [LC 144](https://leetcode.com/problems/binary-tree-preorder-traversal/) | Node, left, right |
| 8 | Postorder Traversal | Easy | [LC 145](https://leetcode.com/problems/binary-tree-postorder-traversal/) | Left, right, node |
| 9 | Path Sum | Easy | [LC 112](https://leetcode.com/problems/path-sum/) | DFS with running sum |
| 10 | Path Sum II (All Paths) | Medium | [LC 113](https://leetcode.com/problems/path-sum-ii/) | Backtracking to collect paths |

### 17.3 BST (Binary Search Tree) Operations

> **Core idea:** For BST: left < node < right. Search O(log n) avg, O(n) worst (unbalanced). Insert/delete maintain invariant.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 11 | Search in BST | Easy | [LC 700](https://leetcode.com/problems/search-in-a-binary-search-tree/) | Exploit BST property |
| 12 | Insert into BST | Medium | [LC 701](https://leetcode.com/problems/insert-into-a-binary-search-tree/) | Maintain BST invariant |
| 13 | Delete Node in BST | Medium | [LC 450](https://leetcode.com/problems/delete-node-in-a-bst/) | Three cases: leaf, one child, two children |
| 14 | Lowest Common Ancestor | Easy | [LC 235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) | Exploit BST: LCA where nodes straddle |
| 15 | Validate BST | Medium | [LC 98](https://leetcode.com/problems/validate-binary-search-tree/) | In-order should be increasing |
| 16 | Kth Smallest in BST | Medium | [LC 230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) | In-order; count |
| 17 | BST to Greater Sum Tree | Medium | [LC 1038](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/) | Reverse in-order (right, node, left) |

### 17.4 Tree Construction

> **Core idea:** Build tree from traversal arrays or array representation.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 18 | Construct from Preorder & Inorder | Medium | [LC 105](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) | Preorder first element is root |
| 19 | Construct from Inorder & Postorder | Medium | [LC 106](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/) | Postorder last element is root |
| 20 | Construct from Level Order | Medium | [GFG](https://www.geeksforgeeks.org/construct-a-binary-tree-from-parent-array/) | BFS-style building |

### 17.5 Tree Queries (Not DP)

> **Core idea:** Query trees for properties: distance, LCA, depth, etc.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 21 | Lowest Common Ancestor | Medium | [LC 236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | Recursive: LCA in left/right |
| 22 | Maximum Depth | Easy | [LC 104](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | 1 + max(left, right) |
| 23 | Minimum Depth | Easy | [LC 111](https://leetcode.com/problems/minimum-depth-of-binary-tree/) | 1 + min(left, right) if both children exist |

---

## 18. TRIE (Prefix Tree)

### 18.1 Insert / Search / StartsWith

> **Core idea:** Tree of characters. Each node's children map = next chars. Mark end of word. O(m) per operation where m = word length.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Implement Trie | Medium | [LC 208](https://leetcode.com/problems/implement-trie-prefix-tree/) | TrieNode with children dict + isEndOfWord flag |
| 2 | Search Suggestions System | Medium | [LC 1268](https://leetcode.com/problems/search-suggestions-system/) | Trie for prefix matching |
| 3 | AutoComplete (Trie) | Medium | [GFG](https://www.geeksforgeeks.org/trie-insert-and-search/) | Prefix-based search |

### 18.2 Word Problems

> **Core idea:** Trie for efficient word lookups, prefix matching, spell-checking.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Word Search II | Hard | [LC 212](https://leetcode.com/problems/word-search-ii/) | Trie + DFS on grid |
| 5 | Implement Word Dictionary | Medium | [LC 211](https://leetcode.com/problems/add-and-search-word-data-structure-design/) | Trie with wildcard support |
| 6 | Word Ladder | Medium | [LC 127](https://leetcode.com/problems/word-ladder/) | BFS on word transformations |
| 7 | Longest Common Prefix | Easy | [LC 14](https://leetcode.com/problems/longest-common-prefix/) | Trie traversal or string comparison |

### 18.3 XOR Trie

> **Core idea:** Trie of binary representations. Efficient XOR queries. Find max/min XOR pair.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 8 | Maximum XOR of Two Numbers | Medium | [LC 421](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/) | XOR Trie to greedily pick opposite bits |
| 9 | Maximum XOR with Element in Array | Hard | [LC 1707](https://leetcode.com/problems/maximum-xor-with-an-element-from-array/) | XOR Trie |

---

## 19. SEGMENT TREE & BINARY INDEXED TREE (Fenwick Tree)

### 19.1 Segment Tree — Range Query & Update

> **Core idea:** Tree where each node represents interval. Supports range query and point/range update in O(log n).
> Build O(n), query/update O(log n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Range Sum Query (Segment Tree) | Medium | [LC 307](https://leetcode.com/problems/range-sum-query-mutable/) | Segment tree for mutable queries |
| 2 | Count of Smaller Numbers After Self | Hard | [LC 315](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) | Segment tree or merge sort |
| 3 | Number of Subarrays with Bounded Maximum | Medium | [LC 795](https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/) | Prefix sum or segment tree |

### 19.2 Binary Indexed Tree (Fenwick Tree)

> **Core idea:** Compact representation supporting prefix sum and point update in O(log n). More space-efficient than segment tree.
> Update: `tree[i] += delta; i += i & (-i)`
> Query: `sum = 0; while i > 0: sum += tree[i]; i -= i & (-i); return sum`

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Range Sum Query (BIT) | Medium | [LC 307](https://leetcode.com/problems/range-sum-query-mutable/) | BIT for O(log n) updates & queries |
| 5 | Create Sorted Array (BIT) | Hard | [LC 1649](https://leetcode.com/problems/create-sorted-array-through-instructions/) | BIT to count smaller/greater |
| 6 | Inversion Count | Hard | [GFG](https://www.geeksforgeeks.org/inversion-count-in-array-using-merge-sort/) | BIT or merge sort |

---

## 20. DISJOINT SET UNION (DSU / Union-Find)

### 20.1 Union-Find with Path Compression

> **Core idea:** Track connected components. `find(x)` = representative of component. `union(x, y)` = merge components.
> With path compression & union by rank: nearly O(1) amortized.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Number of Connected Components | Easy | [LC 323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/) | DSU to count components |
| 2 | Friend Circles | Medium | [LC 547](https://leetcode.com/problems/friend-circles/) | DSU or DFS |
| 3 | Redundant Connection | Medium | [LC 684](https://leetcode.com/problems/redundant-connection/) | Find edge creating cycle via DSU |
| 4 | Redundant Connection II (Directed) | Hard | [LC 685](https://leetcode.com/problems/redundant-connection-ii/) | Handle directed graph |

### 20.2 Weighted DSU

> **Core idea:** Each node tracks distance/weight to representative. Used for constraint satisfaction, potential methods.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 5 | Weighted Union-Find | Hard | [GFG](https://www.geeksforgeeks.org/weighted-union-find-union-by-rank-or-height-with-path-compression/) | Track weights (distances) |

---

## 21. INTERVALS

### 21.1 Merge Intervals

> **Core idea:** Sort by start time. Merge overlapping intervals. O(n log n).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Merge Intervals | Medium | [LC 56](https://leetcode.com/problems/merge-intervals/) | Sort, then merge on overlap |
| 2 | Insert Interval | Medium | [LC 57](https://leetcode.com/problems/insert-interval/) | Insert new interval and merge |
| 3 | Meeting Rooms | Easy | [LC 252](https://leetcode.com/problems/meeting-rooms/) | Check overlap after sorting |

### 21.2 Interval Scheduling

> **Core idea:** Activity selection: sort by end time, greedily pick non-overlapping intervals.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 4 | Non-overlapping Intervals | Medium | [LC 435](https://leetcode.com/problems/non-overlapping-intervals/) | Greedy removal to maximize kept intervals |
| 5 | Video Stitching | Medium | [LC 1024](https://leetcode.com/problems/video-stitching/) | Greedy interval covering |

### 21.3 Interval Queries

> **Core idea:** Given intervals, answer queries about overlaps, coverage, etc.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 6 | Meeting Rooms II | Medium | [LC 253](https://leetcode.com/problems/meeting-rooms-ii/) | Count concurrent meetings: min rooms needed |
| 7 | Minimum Interval to Include Each Query | Hard | [LC 1851](https://leetcode.com/problems/minimum-interval-to-include-each-query/) | Sort intervals, binary search |

---

## 22. MATRIX / 2D ARRAY TECHNIQUES

### 22.1 Matrix Traversal

> **Core idea:** BFS/DFS on 2D grid. Mark visited. O(n * m).

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 1 | Number of Islands | Medium | [LC 200](https://leetcode.com/problems/number-of-islands/) | DFS or BFS on grid |
| 2 | Surrounded Regions | Medium | [LC 130](https://leetcode.com/problems/surrounded-regions/) | DFS from boundary |
| 3 | Rotting Oranges | Medium | [LC 994](https://leetcode.com/problems/rotting-oranges/) | Multi-source BFS |
| 4 | Shortest Path in Binary Matrix | Medium | [LC 1091](https://leetcode.com/problems/shortest-path-in-binary-matrix/) | BFS guaranteed shortest |

### 22.2 Spiral / Rotational Traversal

> **Core idea:** Traverse matrix in spiral order or after rotation. Handle boundaries carefully.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 5 | Spiral Matrix | Medium | [LC 54](https://leetcode.com/problems/spiral-matrix/) | Track 4 boundaries, shrink as traverse |
| 6 | Spiral Matrix II | Medium | [LC 59](https://leetcode.com/problems/spiral-matrix-ii/) | Fill in spiral order |
| 7 | Rotate Image | Medium | [LC 48](https://leetcode.com/problems/rotate-image/) | Transpose then reverse rows |

### 22.3 Matrix Search

> **Core idea:** Sorted matrix; search efficiently.

| # | Problem | Difficulty | Link | Key Concept |
|---|---------|------------|------|-------------|
| 8 | Search in Sorted Matrix | Medium | [LC 74](https://leetcode.com/problems/search-a-2d-matrix/) | Binary search on flattened view |
| 9 | Search in Rotated Sorted Matrix | Medium | [LC 240](https://leetcode.com/problems/search-a-2d-matrix-ii/) | Start from top-right, greedy |

---

## 23. QUICK REFERENCE — Master Algorithm Sheet

| Technique | Time | Space | Use When | Key Problem |
|-----------|------|-------|----------|-------------|
| **Binary Search** | O(log n) | O(1) | Sorted array, monotone property | LC 704 |
| **Two Pointers** | O(n) | O(1) | Opposite ends, fast-slow, in-place | LC 167 |
| **Sliding Window** | O(n) | O(k) or O(alphabet) | Substring/subarray match, min/max | LC 76 |
| **Prefix Sum** | O(n) setup, O(1) query | O(n) | Range sum queries, subarray sums | LC 560 |
| **HashMap** | O(1) avg | O(n) | Frequency, index tracking, anagrams | LC 1 |
| **Sorting** | O(n log n) | O(1) to O(n) | Comparisons, order-dependent logic | LC 912 |
| **Stack** | O(n) | O(n) | Matching, parsing, next greater | LC 496 |
| **Queue** | O(n) | O(n) | BFS, level-order, multi-source | LC 200 |
| **Heap** | O(n log k) for top-k | O(k) | Top-K, Kth extremum, median | LC 347 |
| **Bit Manipulation** | O(n) | O(1) | Single element, XOR properties | LC 136 |
| **Greedy** | Varies | O(1) to O(n) | Optimization with local choices | LC 435 |
| **Backtracking** | O(branching^depth) | O(depth) | Permutations, subsets, constraints | LC 46 |
| **Divide & Conquer** | O(n log n) avg | O(log n) | Quickselect, merge sort, partitioning | LC 215 |
| **String (KMP/Z)** | O(n + m) | O(m) | Pattern matching, substrings | LC 214 |
| **Trie** | O(m) per op | O(alphabet * m * words) | Word lookup, prefix matching, autocomplete | LC 208 |
| **Segment Tree** | O(log n) query/update | O(n) | Mutable range queries | LC 307 |
| **BIT (Fenwick)** | O(log n) query/update | O(n) | Prefix sums with updates | LC 307 |
| **DSU** | O(α(n)) amortized | O(n) | Connected components, cycles | LC 684 |
| **Intervals** | O(n log n) sort | O(n) | Merging, scheduling, coverage | LC 56 |
| **Matrix BFS/DFS** | O(n*m) | O(n*m) | Grid traversal, islands, paths | LC 200 |

---

> **Pro Tips:**
> - Always clarify **constraints**: sorted? duplicates? in-place?
> - **Optimize space** when possible (two-pointer beats HashMap often)
> - **Combine techniques**: sort + two-pointer, prefix sum + HashMap, binary search + greedy
> - **Start simple**, refine: brute force → optimized → final
> - **Test edge cases**: empty, single element, all duplicates, sorted/reversed

---

*Sheet covers ~250 problems across 23 core algorithmic topics. Master these patterns, ace your interviews.*
