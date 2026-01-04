+ Matrix Exponentiation is a technique used to calculate a matrix raised to a power efficiently, that is in logN time. It is mostly used for solving problems related to linear recurrences.

+ Similar to Binary Exponentiation which is used to calculate a number raised to a power, Matrix Exponentiation is used to calculate a matrix raised to a power efficiently.

| Level | Problem Name / Topic | Platform | Key Concept |
| :--- | :--- | :--- | :--- |
| **Easy** | [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) | LeetCode | Replace $O(N)$ DP with $O(\log N)$ Matrix Power. |
| **Medium** | [Climbing Stairs (General Case)](https://leetcode.com/problems/climbing-stairs/) | LeetCode | Solve for $K$ steps using a $K \times K$ transition matrix. |
| **Medium** | [Fibonacci Sum](https://www.spoj.com/problems/FIBOSUM/) | SPOJ | Calculate $\sum_{i=n}^{m} F_i$ using matrix transformation. |
| **Hard** | [Linear Recurrence](https://www.hackerrank.com/challenges/linear-recurrence/problem) | HackerRank | Generalize the matrix for any $k^{th}$ order recurrence. |
| **Hard** | [String Mood](https://codeforces.com/gym/102644/problem/A) | CodeForces | Use matrix exponentiation to find probability in a Markov Chain. |
| **Expert** | [Count Paths (Graph)](https://codeforces.com/gym/102644/problem/B) | CodeForces | Find the number of paths of length $K$ in a graph using $A^K$. |
| **Expert** | [Knight Paths](https://codeforces.com/gym/102644/problem/E) | CodeForces | $64 \times 64$ matrix exponentiation to find knight moves on a board. |
| **Implementation** | [Numerical $e^{At}$](https://github.com/scipy/scipy/blob/v1.11.3/scipy/linalg/_expm_glide.py) | GitHub/SciPy | Code the Padé Approximation (Scaling and Squaring). |

<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/10c03bad-65ab-4f43-b004-156dd20914d3" />

<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/c773044d-f7ed-4d57-9234-6066da44de83" />

<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/7e36f0ef-570d-4cdf-a6f1-94510b07a8b9" />

![Matrix-Exponentiation-1](https://github.com/user-attachments/assets/ecc58a1e-192b-4c0c-b977-32ff02c13840)

![Matrix-Exponentiation-4](https://github.com/user-attachments/assets/6fcfbea9-d57b-469d-b4a7-0ee5b0b47c79)

![Matrix-Exponentiation-8](https://github.com/user-attachments/assets/b6f7c3ed-bcc7-4249-b90b-1f07e3770b40)

![Matrix-Exponentiation-9](https://github.com/user-attachments/assets/67f86812-00d4-4de6-bc4b-119221a8d168)

## Implementation
```
MOD = 10**9 + 7

def multiply(A, B):
    """Multiplies two matrices A and B under modulo."""
    C = [[0, 0], [0, 0]]
    for i in range(2):
        for j in range(2):
            for k in range(2):
                C[i][j] = (C[i][j] + A[i][k] * B[k][j]) % MOD
    return C

def power(A, n):
    """Calculates A^n in O(log n) time."""
    res = [[1, 0], [0, 1]]  # Identity Matrix
    while n > 0:
        if n % 2 == 1:
            res = multiply(res, A)
        A = multiply(A, A)
        n //= 2
    return res

def get_fibonacci(n):
    if n == 0: return 0
    if n == 1: return 1
    
    # Transition matrix for Fibonacci: [[1, 1], [1, 0]]
    T = [[1, 1], [1, 0]]
    T_n = power(T, n - 1)
    
    # The result is the top-left element of T^(n-1) * [F1, F0]
    return T_n[0][0]

# Example: Get 100th Fibonacci number
print(f"100th Fibonacci (mod 10^9+7): {get_fibonacci(100)}")
```
+ Matrix values grow exponentially (literally). Without the modulo (% 10**9 + 7), your computer would quickly run out of memory trying to store a number with thousands of digits, and the math would become extremely slow


<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/c468ad98-6fce-48bb-8fff-9215810fc674" />
