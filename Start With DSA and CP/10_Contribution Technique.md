### Contribution Technique

The "**Contribution Technique**" is an essential, high-level conceptual pattern used to optimize the calculation of aggregated values over all possible subarrays, subsets, or pairs.

It allows you to solve problems that traditionally require $O(N^2)$ or $O(N^3)$ nested loops in linear **$O(N)$ time**.

---

### The Core Mental Shift: Focus on the Element

The central idea is to change your focus from iterating over the results of **subarrays** to calculating the **total contribution** of each individual **element**.
### The Universal Subarray Frequency Formula

For any element at index $i$ in a 0-indexed array of size $n$, its frequency (the number of subarrays it belongs to) is found by multiplying the number of choices for the left boundary by the number of choices for the right boundary.

#### Derivation

* **Choices for Start (Left):** The subarray can start anywhere from index $0$ up to index $i$.
    * Count: i - 0 + 1 = **(i + 1)**
* **Choices for End (Right):** The subarray can end anywhere from index $i$ up to the last index $n-1$.
    * Count: (n - 1) - i + 1 = **(n - i)**

The universal frequency of $arr[i]$ is:
Frequency} = (i + 1)*(n - i)

---

### Categorizing Problems Solved by Contribution

The problems are categorized by how the frequency calculation is handled:

#### 1. Type 1: Simple Frequency Problems (Sum & XOR)

These problems are the most straightforward, using the universal formula directly because the contribution of $arr[i]$ is independent of the value of its neighbors.

| Problem Example | Operator Rule | Solving Approach |
| :--- | :--- | :--- |
| **Sum of Subarray Sums** | Standard Addition: $\sum (\text{Value} \times \text{Freq})$ | Loop $i=0$ to $n-1$. Calculate $\text{Freq}$. Add $\text{arr}[i] \times \text{Freq}$ to total sum. |
| **XOR of Subarray XORs** (Your problem) | Parity Check: $\text{Value}$ if $\text{Freq}$ is Odd, $0$ if $\text{Freq}$ is Even. | Loop $i=0$ to $n-1$. If $(i+1)(n-i)$ is **Odd**, $\text{TotalXOR} \oplus= \text{arr}[i]$. (This simplifies to only XORing elements at even indices when $n$ is odd). |

#### 2. Type 2: Monotonic Stack Frequency Problems (Min & Max)

In this category, the element's contribution is **conditional**. The frequency of $arr[i]$ is no longer the total number of subarrays, but the number of subarrays where $arr[i]$ is the **minimum** (or **maximum**). The simple formula is insufficient.

* **Common Problems:** Sum of Subarray Minimums, Sum of Subarray Maximums.
* **Solving Approach (for Minimums):**
    1.  **Find Boundaries (Pre-calculation):** Use a **Monotonic Stack** in $O(N)$ time to find:
        * **Next Less Element (NLE):** Index of the first smaller element to the left of $i$.
        * **Next Less/Equal Element (NLE):** Index of the first smaller or equal element to the right of $i$. (Handling ties is crucial for unique counting).
    2.  **Define Range:** The boundaries $[ \text{NLE}[i] + 1, \text{NGE}[i] - 1 ]$ define the **exclusive window** where $arr[i]$ is the minimum.
    3.  **Calculate Conditional Frequency:** The new choices for $L$ and $R$ become based on these boundary indices:
        * $L = i - \text{NLE}[i]$
        * $R = \text{NGE}[i] - i$
    4.  **Contribution:** $\text{TotalSum} += \text{arr}[i] \times L \times R$.

#### 3. Type 3: Bitwise Decomposition Problems (OR & AND)

These problems combine the contribution technique with the principle of **Bit Independence**.

* **Common Problems:** Sum of Bitwise OR of all subarrays.
* **Solving Approach (for Bitwise OR Sum):**
    1.  **Outer Loop:** Iterate through each bit position $k$ from 0 to 31.
    2.  **Decomposition:** For the current bit $k$, create a conceptual binary array where $temp[i] = 1$ if the $k$-th bit of $arr[i]$ is set, and $0$ otherwise.
    3.  **Contribution on Binary Array:** The problem now is to find the total count of subarrays in the $temp$ array that contain **at least one 1** (because $0 \mid 1 = 1$). This is solved in $O(N)$ by using dynamic programming or tracking the index of the **last $0$** seen.
        * Total Subarrays - (Subarrays consisting only of 0s) = Subarrays with at least one 1.
    4.  **Aggregation:** Let $\text{Count}_k$ be the number of subarrays with the $k$-th bit set. The total contribution is $\text{TotalSum} += \text{Count}_k \times 2^k$.

---

### Approach Checklist for Contribution Problems

Whenever you encounter a "Compute [Operation] over all Subarrays" problem, use this checklist:

1.  **Analyze the Operator:** Does the operator (Sum, XOR, Min, OR) allow for a simple frequency calculation?
2.  **Calculate Frequency ($L \times R$):**
    * **Simple:** Use (i+1) \times (n-i). (Type 1)
    * **Conditional:** Use a **Monotonic Stack** to find the valid $L$ and $R$ bounds. (Type 2)
    * **Bitwise:** Decompose the problem into 32 separate subproblems. (Type 3)
3.  **Aggregate:** Apply the operator's rule (e.g., multiply by value, or check parity).
