## Dijkstra's Algorithm: Code Review



### 1. The Fix
In your `heapq.heappush(q, (d[i[0]], i[1]))`, you are pushing `i[1]` as the node. However, in your adjacency list, `i[0]` is the neighbor and `i[1]` is the weight.

**Corrected Line:**
`heapq.heappush(q, (d[i[0]], i[0]))`

### 2. Optimized Implementation (Raw Markdown)

```python
import heapq

class Solution:
    def dijkstra(self, V, edges, src):
        # 1. Build Adjacency List
        adj = [[] for _ in range(V)]
        for u, v, w in edges:
            adj[u].append((v, w))
            adj[v].append((u, w))
            
        # 2. Initialize distances and Priority Queue
        dist = [float('inf')] * V
        dist[src] = 0
        pq = [(0, src)] # (distance, node)
        
        while pq:
            current_dist, u = heapq.heappop(pq)
            
            # If we found a shorter path already, skip this stale entry
            if current_dist > dist[u]:
                continue
                
            for v, weight in adj[u]:
                if dist[v] > current_dist + weight:
                    dist[v] = current_dist + weight
                    heapq.heappush(pq, (dist[v], v))
                    
        return dist

## Floyd-Warshall Algorithm: The "All-Pairs" Approach

Floyd-Warshall is a **Dynamic Programming** algorithm. Instead of traversing edges from one node, it systematically considers every node $k$ as an intermediate stepping stone between every pair of nodes $(i, j)$.

### 1. How it Works (The Core Logic)
The algorithm maintains a 2D matrix $D$ where $D[i][j]$ is the shortest distance from $i$ to $j$. For every vertex $k$, it checks:
*"Is it shorter to go from $i$ to $j$ directly, or by going $i \to k \to j$?"*

**The Formula:**
$$D[i][j] = \min(D[i][j], D[i][k] + D[k][j])$$



---

### 2. Why use Floyd-Warshall?
* **All-Pairs:** You get a complete map of every distance in the graph in one execution.
* **Negative Edges:** Like Bellman-Ford, it handles negative weights correctly.
* **Simplicity:** The code is incredibly short (three nested loops).
* **Dense Graphs:** It is very efficient for graphs where most nodes are connected to each other.

---

### 3. Comparison of Shortest Path Algorithms

| Feature | Dijkstra | Bellman-Ford | Floyd-Warshall |
| :--- | :--- | :--- | :--- |
| **Type** | Single-Source | Single-Source | **All-Pairs** |
| **Complexity** | $O(E \log V)$ | $O(V \cdot E)$ | $O(V^3)$ |
| **Negative Edges** | No | Yes | **Yes** |
| **Negative Cycles**| No | Detects them | **Detects them** |
| **Best for...** | Large, positive graphs | Graphs with negative edges | Small, dense graphs |

[Image comparing Dijkstra, Bellman-Ford, and Floyd-Warshall performance curves]

---

### 4. Implementation in Python
```python
def floyd_warshall(V, adj_matrix):
    # Initialize distance matrix with the input adjacency matrix
    dist = [row[:] for row in adj_matrix]

    # Triple Nested Loop (The heart of the algorithm)
    for k in range(V):          # Intermediate node
        for i in range(V):      # Source node
            for j in range(V):  # Destination node
                # Update if path through k is shorter
                dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
    
    return dist
