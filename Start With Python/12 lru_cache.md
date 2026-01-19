# Python `@lru_cache` Deep Dive

The `@lru_cache` decorator (from `functools`) is a built-in tool for **memoization**. It saves the results of expensive function calls so that when the same inputs occur again, the function returns the stored value instantly instead of recalculating it.

---

### 1. The Workflow
When you call a function decorated with `@lru_cache(None)`:
1. **The Check:** The assistant looks at the arguments you passed (e.g., `i=3`, `current_sum=10`).
2. **The Look-up:** It checks its internal dictionary (hash map) to see if it has seen these exact arguments before.
3. **The Shortcut:** * **If YES (Cache Hit):** It immediately returns the stored result without ever running the code inside your function.
   * **If NO (Cache Miss):** It lets the function run, waits for the result, saves that result in its dictionary, and then returns it to you.



---

### 2. What does "LRU" stand for?
**LRU** stands for **Least Recently Used**.
* **Infinite Cache:** In Dynamic Programming (DP), we usually use `@lru_cache(None)`. This means the cache size is infinite; it will remember everything until your program stops.
* **Limited Cache:** If you use `@lru_cache(maxsize=128)`, the assistant only has space for 128 entries. Once the cache is full, it erases the **oldest, least-used entry** to make room for a new one.

---

### 3. Comparing Manual DP vs. `lru_cache`
Using the **Subset Sum** problem as an example:

#### The Manual Way:
```python
if dp[sum][i] != -1:
    return dp[sum][i]
# ... calculate result ...
dp[sum][i] = result
return result
```

#### The `lru_cache` Way:
```python
from functools import lru_cache

class Solution:
    def isSubsetSum(self, arr, sum_val):
        @lru_cache(None) # Replaces the manual DP table entirely
        def rec(i, current_sum):
            if current_sum == 0: return True
            if i >= len(arr): return False
            
            # The cache handles the "if result in dp" check automatically
            res = False
            if current_sum >= arr[i]:
                res = rec(i + 1, current_sum - arr[i])
            return res or rec(i + 1, current_sum)

        return rec(0, sum_val)
```

---

### 4. Pros and Cons

| Feature | Manual DP Table | `@lru_cache` |
| :--- | :--- | :--- |
| **Effort** | High (indices/initialization) | Extremely Low (1 line) |
| **Readability** | Messy (table lookups) | Very Clean (pure recursion) |
| **Control** | Full control over memory | Hidden management |
| **Interview** | **Required** (shows logic) | **Bonus** (shows Python mastery) |

---

### 5. Two Strict Rules for `lru_cache`
1. **Arguments must be Hashable:** You cannot pass a `list` into a cached function (like `rec(arr, i, sum)`) because lists can change. Pass the list as a `tuple` or keep the list as a class variable so the cache doesn't have to "look" at it.
2. **Function must be Deterministic:** For the same input, it must always return the same output.

---

### ⚠️ Important Warning for DP Learners
**Do not use `lru_cache` yet.** While tempting, you may fail the **Tabulation** (Iterative) step of your learning path if you don't practice building physical 2D tables manually. The table helps you visualize the direction of dependencies (e.g., "I need the values from the previous row to calculate this row").

---

### 6. Cache Management Methods
* **`func.cache_info()`**: Returns hits, misses, maxsize, and currsize.
* **`func.cache_clear()`**: Immediately empties the entire cache.
