# 📚 Permutation & Combination — Complete JEE Notes
### For JEE Mains & Advanced | By Topic + Tips & Tricks

---

## 📋 Table of Contents

1. [Fundamental Principle of Counting](#1-fundamental-principle-of-counting)
2. [Factorials](#2-factorials)
3. [Permutations](#3-permutations)
4. [Combinations](#4-combinations)
5. [Special Cases in Permutations](#5-special-cases-in-permutations)
6. [Special Cases in Combinations](#6-special-cases-in-combinations)
7. [Circular Permutations](#7-circular-permutations)
8. [Distribution Problems](#8-distribution-problems)
9. [Derangements](#9-derangements)
10. [Multinomial Theorem](#10-multinomial-theorem)
11. [Important Results & Identities](#11-important-results--identities)
12. [Tips, Tricks & Shortcuts](#12-tips-tricks--shortcuts)
13. [JEE-Style Problem Patterns](#13-jee-style-problem-patterns)
14. [Common Mistakes to Avoid](#14-common-mistakes-to-avoid)
15. [Quick Formula Sheet](#15-quick-formula-sheet)

---

## 1. Fundamental Principle of Counting

### 1.1 Multiplication Principle (AND Rule)
> If one task can be done in **m** ways and a second task can be done in **n** ways, then **both** tasks together can be done in **m × n** ways.

**Example:** 3 shirts and 4 pants → 3 × 4 = **12 outfits**

### 1.2 Addition Principle (OR Rule)
> If one task can be done in **m** ways OR another task in **n** ways (mutually exclusive), then total ways = **m + n**.

**Example:** Travel by bus (3 routes) OR train (2 routes) → 3 + 2 = **5 ways**

### 1.3 Combined Principle
> Real problems use BOTH principles. Break the task into steps (use ×), then combine choices (use +).

**Example:** Form a 3-digit number from {1,2,3,4,5} where first digit is odd OR even.
- First digit odd (1,3,5): 3 × 5 × 5 = 75
- First digit even (2,4): 2 × 5 × 5 = 50
- Total = 75 + 50 = **125**

---

## 2. Factorials

### Definition
$$n! = n \times (n-1) \times (n-2) \times \cdots \times 2 \times 1$$

### Key Values to Memorize

| n | n! |
|---|------|
| 0 | 1 |
| 1 | 1 |
| 2 | 2 |
| 3 | 6 |
| 4 | 24 |
| 5 | 120 |
| 6 | 720 |
| 7 | 5040 |
| 8 | 40320 |
| 9 | 362880 |
| 10 | 3628800 |

### Important Properties
- **0! = 1** (by definition — memorize this!)
- **n! = n × (n-1)!**
- **n! / (n-r)! = n(n-1)(n-2)···(n-r+1)** (r terms)

### Trailing Zeros in n! (JEE Trick)
Number of trailing zeros = Number of times 5 divides n!

$$\text{Trailing zeros in } n! = \left\lfloor \frac{n}{5} \right\rfloor + \left\lfloor \frac{n}{25} \right\rfloor + \left\lfloor \frac{n}{125} \right\rfloor + \cdots$$

**Example:** Trailing zeros in 100! = ⌊100/5⌋ + ⌊100/25⌋ = 20 + 4 = **24**

---

## 3. Permutations

### Definition
An **arrangement** of objects where **order matters**.

$$^nP_r = \frac{n!}{(n-r)!} = n(n-1)(n-2)\cdots(n-r+1) \quad (r \text{ terms})$$

### Conditions
- n = total items, r = items selected (r ≤ n)
- All items are **distinct**
- **Repetition NOT allowed** (unless stated)

### Standard Results

| Scenario | Formula |
|----------|---------|
| Arrange all n distinct items | n! |
| Select r from n distinct, arrange | ⁿPᵣ = n!/(n-r)! |
| Arrange n items with repetition allowed | nʳ |
| ⁿP₀ | 1 |
| ⁿP₁ | n |
| ⁿPₙ | n! |
| ⁿPₙ₋₁ | n! |

### Example
How many 3-letter words from ENGLISH letters (no repeat)?
$$^{26}P_3 = 26 \times 25 \times 24 = 15600$$

---

## 4. Combinations

### Definition
A **selection** of objects where **order does NOT matter**.

$$^nC_r = \binom{n}{r} = \frac{n!}{r!(n-r)!}$$

### Key Properties

| Property | Statement |
|----------|-----------|
| Symmetry | ⁿCᵣ = ⁿCₙ₋ᵣ |
| Boundary | ⁿC₀ = ⁿCₙ = 1 |
| Unit | ⁿC₁ = n |
| Pascal's Identity | ⁿCᵣ = ⁿ⁻¹Cᵣ₋₁ + ⁿ⁻¹Cᵣ |
| Relation | ⁿPᵣ = r! × ⁿCᵣ |
| Vandermonde's | ᵐ⁺ⁿCᵣ = Σ ᵐCₖ × ⁿCᵣ₋ₖ |

### Symmetry Trick
> If ⁿCₓ = ⁿCᵧ then either **x = y** or **x + y = n**

**Example:** If ¹²Cₓ = ¹²C₈, then x = 8 or x = 4.

---

## 5. Special Cases in Permutations

### 5.1 Permutations with Repetition
Arrange n items where:
- Item₁ repeats p times
- Item₂ repeats q times
- Item₃ repeats r times, etc.

$$\text{Total arrangements} = \frac{n!}{p! \cdot q! \cdot r! \cdots}$$

**Example:** Arrangements of MISSISSIPPI (11 letters: M=1, I=4, S=4, P=2)
$$= \frac{11!}{1! \cdot 4! \cdot 4! \cdot 2!} = 34650$$

### 5.2 Restricted Permutations

#### Always Together (Treat as a block)
Bundle the "together" items as one unit.
- n items, k must be together → (n-k+1)! × k! arrangements

**Example:** 6 people in a row, A and B always together:
→ Treat AB as 1 unit: 5! × 2! = 120 × 2 = **240**

#### Never Together (Total – Always Together)
**Never together = Total – Always Together**

**Example:** 6 people, A and B never together:
→ 6! − 5! × 2! = 720 − 240 = **480**

#### Alternating Arrangement (M and F alternate)
- m men, n women
- If m = n: 2 × m! × n! (man or woman can start)
- If m = n+1: m! × n! (man must start)

### 5.3 Positions with Restrictions

#### At Least One Fixed Position
Use complementary counting:
> At least one specific condition = Total − None satisfying the condition

#### Specific Positions (Odd/Even seats)
**Example:** In ABCDE, vowels (A, E) must occupy odd positions (1, 3, 5):
- Choose 2 odd positions from 3 for vowels: ³P₂ = 6
- Arrange 3 consonants in remaining 3 positions: 3! = 6
- Total = 6 × 6 = **36**

### 5.4 n-digit Numbers

#### No Leading Zero
- First digit can't be 0
- First digit: (total digits − 1) choices
- Remaining: fill normally

**Example:** 4-digit numbers from {0,1,2,3,4,5} without repetition:
- First digit: 5 choices (1-5)
- Remaining 3: ⁵P₃ = 60
- Total = 5 × 60 = **300**

#### Divisibility Conditions
- **Divisible by 2**: last digit must be even
- **Divisible by 5**: last digit must be 0 or 5
- **Divisible by 4**: last 2 digits form a number divisible by 4
- **Divisible by 8**: last 3 digits divisible by 8
- **Divisible by 3**: sum of digits divisible by 3

---

## 6. Special Cases in Combinations

### 6.1 At Least / At Most

| Condition | Strategy |
|-----------|----------|
| At least r | Total − (less than r cases) |
| At most r | Sum individual cases (0 to r) |
| Exactly r | Direct: ⁿCᵣ |

**Example:** From 10 items, select at least 1:
$$2^{10} - 1 = 1023$$

### 6.2 Selecting from Different Groups

Choose r from group A (size m) and s from group B (size n):
$$= {}^mC_r \times {}^nC_s$$

**Example:** Committee of 3 men and 2 women from 5 men and 4 women:
$${}^5C_3 \times {}^4C_2 = 10 \times 6 = 60$$

### 6.3 Combinations with Restrictions

#### Certain Items Always Included
Treat included items as already chosen, select remaining from rest.

**Example:** 5 from 12, with A always included:
$${}^{11}C_4 = 330$$

#### Certain Items Always Excluded
Simply remove excluded items from the pool.

**Example:** 5 from 12, with B always excluded:
$${}^{11}C_5 = 462$$

#### At Least One From a Subgroup
$$= \text{Total} - \text{(None from subgroup)}$$

### 6.4 Identical Items

Number of ways to select r items from n **identical** items = **1** (only one way)

Number of ways to select at most n identical items = n + 1 (0, 1, 2, ..., n)

---

## 7. Circular Permutations

### 7.1 Basic Circular Arrangement
For n distinct objects in a circle:
$$\text{Arrangements} = (n-1)!$$

> **Why?** Fix one person's position to remove rotational equivalence.

### 7.2 Clockwise vs Anticlockwise
- If CW and ACW are **different** (necklaces with faces): (n-1)!
- If CW and ACW are **same** (necklaces, keyrings): (n-1)!/2

### 7.3 Relative Order Matters
n people around a table, but in chairs labeled 1 to n: This is LINEAR, not circular → n! arrangements.

### 7.4 Circular with Restrictions

#### Some People Always Together (Circular)
Bundle k people as a block: (n−k+1−1)! × k! = (n−k)! × k!

**Example:** 6 people around table, A and B always together:
= (6−2)! × 2! = 4! × 2 = 48

#### Some People Never Together (Circular)
= Total circular − Together circular

**Example:** 6 people, A and B never together:
= (6−1)! − (6−2)! × 2! = 120 − 48 = **72**

### 7.5 Garland / Necklace Problems
Beads arranged in circle (no up/down difference):
$$= \frac{(n-1)!}{2}$$

---

## 8. Distribution Problems

### 8.1 Distributing Distinct Objects into Distinct Groups

| Condition | Formula |
|-----------|---------|
| n distinct → r distinct groups (any can be empty) | rⁿ |
| n distinct → r distinct groups (none empty) | Inclusion-Exclusion |
| n distinct → r identical groups | Stirling Numbers |

### 8.2 Distributing Identical Objects (Stars and Bars)

| Condition | Formula |
|-----------|---------|
| n identical → r distinct groups (empty groups allowed) | ⁿ⁺ʳ⁻¹Cᵣ₋₁ |
| n identical → r distinct groups (none empty) | ⁿ⁻¹Cᵣ₋₁ |
| n identical → r identical groups | Partition function (advanced) |

**Stars and Bars Method:**
> Distributing n identical balls into r distinct boxes = distributing n among r = placing (r−1) dividers among n balls.

**Example:** x₁ + x₂ + x₃ = 10, where xᵢ ≥ 0:
$${}^{10+3-1}C_{3-1} = {}^{12}C_2 = 66$$

**Example:** x₁ + x₂ + x₃ = 10, where xᵢ ≥ 1:
Substitute yᵢ = xᵢ − 1: y₁ + y₂ + y₃ = 7, yᵢ ≥ 0
$${}^{7+3-1}C_{3-1} = {}^9C_2 = 36$$

### 8.3 Distributing Objects into Groups of Fixed Size

Divide 2n people into 2 equal groups:
$$\frac{(2n)!}{(n!)^2 \cdot 2!}$$

Divide 2n people into 2 **named/distinct** groups of n each:
$$\frac{(2n)!}{n! \cdot n!} = {}^{2n}C_n$$

---

## 9. Derangements

### Definition
A **derangement** is a permutation where **no element appears in its original position**.

### Formula (Subfactorial)
$$D(n) = !n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}$$

Or equivalently:
$$D(n) = n!\left(1 - \frac{1}{1!} + \frac{1}{2!} - \frac{1}{3!} + \cdots + \frac{(-1)^n}{n!}\right)$$

### Recurrence Relation
$$D(n) = (n-1)[D(n-1) + D(n-2)]$$

### Values to Memorize

| n | D(n) |
|---|------|
| 1 | 0 |
| 2 | 1 |
| 3 | 2 |
| 4 | 9 |
| 5 | 44 |
| 6 | 265 |

### Application
At least one in original position:
= Total − D(n) = n! − D(n)

Exactly k elements in original position:
$$= {}^nC_k \times D(n-k)$$

---

## 10. Multinomial Theorem

### Coefficient of a Term
In the expansion of (x₁ + x₂ + ... + xₘ)ⁿ, the number of terms is:
$${}^{n+m-1}C_{m-1}$$

Coefficient of x₁^r₁ · x₂^r₂ · ... · xₘ^rₘ (where r₁+r₂+...+rₘ = n):
$$\frac{n!}{r_1! \cdot r_2! \cdots r_m!}$$

### Number of Terms
In (a + b + c)ⁿ: Number of distinct terms = ⁿ⁺²C₂

---

## 11. Important Results & Identities

### Sum of Combinations
$$\sum_{r=0}^{n} {}^nC_r = 2^n$$

$$\sum_{r=0}^{n} {}^nC_r x^r = (1+x)^n$$

$${}^nC_0 + {}^nC_2 + {}^nC_4 + \cdots = 2^{n-1} \quad \text{(even terms)}$$

$${}^nC_1 + {}^nC_3 + {}^nC_5 + \cdots = 2^{n-1} \quad \text{(odd terms)}$$

### Weighted Sum
$$\sum_{r=0}^{n} r \cdot {}^nC_r = n \cdot 2^{n-1}$$

$$\sum_{r=0}^{n} r^2 \cdot {}^nC_r = n(n+1)2^{n-2}$$

### Product Identity
$${}^nC_r \times {}^rC_k = {}^nC_k \times {}^{n-k}C_{r-k}$$

### Pascal's Triangle Properties
- Row n (starting from row 0): entries are ⁿC₀, ⁿC₁, ..., ⁿCₙ
- Each entry = sum of two entries above it
- Sum of row n = 2ⁿ
- Alternating sum of row n = 0 (for n > 0)

### Selecting from n Points
- **Lines**: ⁿC₂ (any 2 points form a line, assuming no 3 collinear)
- **Triangles**: ⁿC₃ (any 3 non-collinear points form a triangle)
- **Diagonals of polygon**: ⁿC₂ − n

**If k points are collinear:**
- Lines = ⁿC₂ − ᵏC₂ + 1
- Triangles = ⁿC₃ − ᵏC₃

---

## 12. Tips, Tricks & Shortcuts

### Tip 1: DECIDE: Permutation or Combination?
> Ask: **"Does order matter?"**
> - Yes → Permutation
> - No → Combination

**Trick:** "Select" = Combination. "Arrange/Order/Sequence" = Permutation.

### Tip 2: Treat Together Items as a Block
When items must be **adjacent**, glue them into a single block. Then:
- Count the blocks as (n−k+1) objects: arrange them in (n−k+1)! ways
- Internally arrange the block: k! ways

### Tip 3: Never Together = Total − Always Together
Much easier than placing items with gaps.

### Tip 4: Gap Method for Non-Adjacent Items
To place r items such that **no two are adjacent**:
1. First arrange the remaining (n−r) items: (n−r)! ways
2. There are (n−r+1) gaps created
3. Choose r gaps: ⁽ⁿ⁻ʳ⁺¹⁾Cᵣ ways
4. Arrange r items in those gaps: r! ways

$$\text{Total} = (n-r)! \times {}^{n-r+1}C_r \times r!$$

**Example:** 5 boys, 4 girls in a row, no two girls adjacent:
- Arrange 5 boys: 5! = 120
- 6 gaps formed (before, between, after boys)
- Choose 4 gaps for girls: ⁶C₄ = 15
- Arrange 4 girls: 4! = 24
- Total = 120 × 15 × 24 = **43200**

### Tip 5: Complementary Counting
> **At least one = Total − None**

Use when "at least 1" condition appears. Always easier!

**Example:** Probability that at least 2 people share a birthday (complementary is easier).

### Tip 6: Fixing One Element in Circular Permutation
Always fix the **most restricted** person or the **reference point** first.

### Tip 7: Identical vs Distinct — the Critical Question
- Are the objects identical or distinct?
- Are the boxes/groups identical or distinct?
This changes the formula completely!

### Tip 8: Use Inclusion-Exclusion
For "at least one from each group" or overlapping conditions:
$$|A \cup B| = |A| + |B| - |A \cap B|$$
$$|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |B \cap C| - |A \cap C| + |A \cap B \cap C|$$

### Tip 9: Stars and Bars Summary
- "Distribute n identical items among r groups (empty allowed)": ⁽ⁿ⁺ʳ⁻¹⁾Cᵣ₋₁
- "Each group gets at least 1": ⁽ⁿ⁻¹⁾Cᵣ₋₁

> **Mnemonic:** "n identical, r boxes, empty ok → (n+r−1) choose (r−1)"

### Tip 10: Rank of a Word
To find rank of a word in dictionary order:
1. Count words starting with letters before the first letter of your word
2. Fix first letter, count words starting with letters before second letter
3. Continue till word is uniquely determined
4. Add 1

**Example:** Rank of CABLE among all permutations of ABCLE:
- Words starting with A: 4! = 24
- Words starting with B: 4! = 24
- Words starting with C, then A: 3! = 6
- Words starting with CA, then B: 2! = 2
- Words starting with CAB, then L: 1! = 1
- CABLE itself: 1
- Rank = 24 + 24 + 6 + 2 + 1 = **57**

### Tip 11: ⁿCᵣ Symmetry for Quick Calculation
$${}^nC_r = {}^nC_{n-r}$$

Always compute with the smaller of r and (n−r):
$${}^{20}C_{17} = {}^{20}C_3 = \frac{20 \times 19 \times 18}{3!} = 1140$$

### Tip 12: Divisor Counting
If n = p₁^a₁ · p₂^a₂ · ... · pₖ^aₖ, then:
- Number of divisors = (a₁+1)(a₂+1)···(aₖ+1)
- Number of ways to write n = A × B (ordered): same as divisors
- Number of ways (unordered): (divisors + 1)/2 if not perfect square, or divisors/2 + ½ for perfect squares

---

## 13. JEE-Style Problem Patterns

### Pattern 1: Committee Problems
"Form a committee of r from n people such that at least k women are included"
→ Split by cases: exactly k women, k+1 women, ..., min(total women, r) women

### Pattern 2: Word Formation
"How many 4-letter words from ABCDE with at least one vowel?"
→ Total 4-letter words − 4-letter words with no vowels

### Pattern 3: Polygon Problems
For a convex n-gon:
- **Diagonals** = ⁿC₂ − n = n(n−3)/2
- **Triangles (vertices on polygon)** = ⁿC₃
- **Triangles with exactly one side of polygon** = n × (n−4)
- **Triangles with exactly two sides of polygon** = n
- **Triangles with no side of polygon** = ⁿC₃ − n(n−4) − n

### Pattern 4: Grid/Path Problems
Number of shortest paths from (0,0) to (m,n) going only right or up:
$$= {}^{m+n}C_m = {}^{m+n}C_n$$

### Pattern 5: Number Theory Combinations
"How many numbers from 1 to 1000 are divisible by 3 or 5?"
→ Use Inclusion-Exclusion:
|3| + |5| − |15|

### Pattern 6: Identical Distribution with Constraints
x₁ + x₂ + x₃ + x₄ = 20, where 2 ≤ xᵢ ≤ 8:
→ Substitute yᵢ = xᵢ − 2 (lower bound shift): y₁+y₂+y₃+y₄ = 12, 0 ≤ yᵢ ≤ 6
→ Use Inclusion-Exclusion for upper bound

### Pattern 7: Counting Subsets
Subsets of {1, 2, ..., n} with sum S: List approach or generating functions (Advanced).

**Key results:**
- Total subsets of n-element set = 2ⁿ
- Non-empty subsets = 2ⁿ − 1
- Subsets of size r = ⁿCᵣ

---

## 14. Common Mistakes to Avoid

### Mistake 1: Mixing Up Permutation and Combination
> "Select 3 from 10" = ¹⁰C₃ (combination)
> "Arrange 3 from 10" = ¹⁰P₃ (permutation)

### Mistake 2: Forgetting 0! = 1
ⁿPₙ = n!/(n−n)! = n!/0! = n!/1 = n! ✓

### Mistake 3: Circular vs Linear
Linear: n objects → n! arrangements
Circular: n objects → (n−1)! arrangements (fix one)

### Mistake 4: Necklace vs Circular Arrangement
Necklace (no designated start, can flip): (n−1)!/2
Round table (no flip): (n−1)!

### Mistake 5: Identical Objects Treated as Distinct
If 3 red balls are identical, ³C₁ ≠ 3. There's only 1 way to choose 1 red ball.

### Mistake 6: Double Counting in Complementary Method
Always verify your "forbidden" cases don't overlap.

### Mistake 7: Not Accounting for Internal Arrangement of Groups
When dividing into groups, if groups are **labeled/named**, multiply by (number of groups)!.

### Mistake 8: Ignoring the Upper Bound in Stars & Bars
If xᵢ ≤ M, you must apply Inclusion-Exclusion or shift variables.

### Mistake 9: Word Rank Off by One
The rank of the word itself is 1, not 0. Always add 1 at the end.

### Mistake 10: Overcounting Symmetrical Arrangements
When arranging identical objects in a circular manner, be careful about rotational symmetry.

---

## 15. Quick Formula Sheet

### Permutations

| Formula | Use |
|---------|-----|
| n! | All n distinct objects arranged |
| n!/(n-r)! = ⁿPᵣ | r from n distinct, ordered |
| n!/(p!q!r!···) | n objects with repeats p, q, r, ... |
| nʳ | r items from n, repetition allowed |
| (n-1)! | Circular, n distinct |
| (n-1)!/2 | Necklace/keychain |

### Combinations

| Formula | Use |
|---------|-----|
| n!/(r!(n-r)!) = ⁿCᵣ | r from n, unordered |
| 2ⁿ | All subsets of n elements |
| 2ⁿ − 1 | Non-empty subsets |
| ⁽ⁿ⁺ʳ⁻¹⁾Cᵣ₋₁ | n identical into r distinct groups (empty ok) |
| ⁽ⁿ⁻¹⁾Cᵣ₋₁ | n identical into r distinct groups (none empty) |

### Derangements

| Formula | Use |
|---------|-----|
| D(n) = n!(1 − 1/1! + 1/2! − ... ± 1/n!) | All items displaced |
| D(n) = (n−1)[D(n−1) + D(n−2)] | Recurrence |

### Geometry Counting

| Scenario | Formula |
|----------|---------|
| Lines from n points | ⁿC₂ |
| Triangles from n points | ⁿC₃ |
| Diagonals of n-gon | ⁿC₂ − n = n(n−3)/2 |
| Shortest grid paths (m,n) | ⁽ᵐ⁺ⁿ⁾Cₘ |

### Number Counting

| Scenario | Formula |
|----------|---------|
| r-digit numbers from n digits (no 0, no repeat) | ⁿPᵣ |
| r-digit numbers from n digits (with 0, no repeat) | (n−1)×ⁿ⁻¹Pᵣ₋₁ |
| Trailing zeros in n! | Σ ⌊n/5ᵏ⌋ |
| Divisors of p₁^a₁·p₂^a₂ | (a₁+1)(a₂+1)··· |

---

## 🎯 Final Revision Checklist

- [ ] Know when to use P vs C (order matters?)
- [ ] Master the gap method for non-adjacent problems
- [ ] Complementary counting reflex (at least one = total − none)
- [ ] Stars and Bars for distribution problems
- [ ] Derangement values D(1) to D(6)
- [ ] Circular arrangement = (n−1)! and necklace = (n−1)!/2
- [ ] Memorize 0! to 10! values
- [ ] Sum of ⁿCᵣ = 2ⁿ and its variants
- [ ] Pascal's Identity: ⁿCᵣ = ⁿ⁻¹Cᵣ₋₁ + ⁿ⁻¹Cᵣ
- [ ] Diagonal formula for n-gon: n(n−3)/2
- [ ] Grid path: ⁽ᵐ⁺ⁿ⁾Cₘ
- [ ] Rank of a word method
- [ ] Inclusion-Exclusion for complex constraints

---

> **Best of luck for JEE Mains & Advanced! 🚀**
> *Practice 10+ problems per topic daily. The key to P&C is pattern recognition — once you identify the type, the formula follows naturally.*
