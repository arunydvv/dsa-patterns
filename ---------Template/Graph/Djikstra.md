
# 📌 Dijkstra’s Algorithm


Dijkstra’s algorithm finds the **shortest distance from a single source node to all other nodes in a weighted, connected graph** with **non-negative edge weights**.

It uses a **greedy approach with a priority queue (min-heap)** to always expand the nearest unvisited node.

---

## ✅ Key Concepts & Invariants

| Concept | Explanation |
|:----------------|:--------------------------------------------------|
| Multiple PQ entries allowed | Yes — because Java’s PriorityQueue has no efficient decrease-key operation |
| When is a node’s shortest distance finalized? | **The first time it is dequeued from the priority queue, and the current distance equals `dist[node]`** |
| How to skip stale entries? | `if (current.distance > dist[node]) continue;` |
| What order does PQ process nodes in? | Always processes the node with the **smallest tentative distance** first |
| Why greedy works here? | Because once a node’s min distance is finalized, no shorter path can reach it later (for non-negative edge weights) |

---

## ✅ Standard Dijkstra Code (Java)

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.PriorityQueue;

class Pair implements Comparable<Pair> {
    int distance, node;
    Pair(int d, int n) {
        this.distance = d;
        this.node = n;
    }

    @Override
    public int compareTo(Pair other) {
        return this.distance - other.distance;
    }
}

public class DijkstraTemplate {
    void Dijkstra(int source, int[] dist, List<List<int[]>> adj) {
        PriorityQueue<Pair> pq = new PriorityQueue<>();
        pq.add(new Pair(0, source));
        dist[source] = 0;

        while (!pq.isEmpty()) {
            Pair current = pq.poll();
            int node = current.node, soFar = current.distance;

            // Skip if this is an outdated (stale) entry
            if (soFar > dist[node]) continue;

            for (int[] neighbour : adj.get(node)) {
                int next = neighbour[0], nextWeight = neighbour[1];
                if (dist[next] > soFar + nextWeight) {
                    dist[next] = soFar + nextWeight;
                    pq.add(new Pair(dist[next], next));
                }
            }
        }
    }
}

```


# 📌 Dijkstra’s Algorithm — Use-Case Summary 🚀

This document summarizes common use-cases and applications of **Dijkstra’s Algorithm** in graph problems, especially competitive programming and coding interviews.

---

## ✅ Use-Cases in Problems 🔥

| Problem Type                                | Dijkstra Application                                                                 |
|:--------------------------------------------|:-------------------------------------------------------------------------------------|
| **Single-source shortest path**             | Classic application in road networks, games, and grid pathfinding problems.          |
| **Multiple queries for shortest path**      | Precompute shortest distances from a source using Dijkstra, store in `dist[]`, and directly answer queries in **O(1)**. |
| **Finding all shortest paths passing through edges** | Run Dijkstra twice — once from source and once from destination — then check for each edge whether it lies on any shortest path using combined distances. |
| **Weighted graphs with non-negative weights** | Dijkstra is **safe, efficient, and optimal** when graph edges have non-negative weights. |
| **Replace BFS in weighted graphs**          | Whenever BFS won’t work because of edge weights (since BFS assumes uniform weights), replace it with Dijkstra for accurate shortest path results. |

---

## 📌 When to Use Dijkstra?

✅ If the graph is **weighted and has non-negative edge weights**  
✅ When you need **shortest distances from a single source to all other nodes**  
✅ When multiple shortest path queries are asked from a single or fixed source  
✅ When you need to check if an edge or node lies on a shortest path  

---

## 📌 Related Algorithms  

| Algorithm      | Use-Case                                      |
|:---------------|:------------------------------------------------|
| **Bellman-Ford** | Single-source shortest path with negative weights |
| **Floyd-Warshall** | All-pairs shortest path (dense graphs or small N ≤ 500) |
| **0-1 BFS**     | When all weights are either 0 or 1 |

---

## 📌 Example Problems  

- **LeetCode 743 — Network Delay Time**
- **LeetCode 1976 — Number of Ways to Arrive at Destination**
- **CSES — Shortest Routes I**
- **Codeforces — Delivery Time Problems**
- **LeetCode 1631 — Path with Minimum Effort**



## ✅ Summary  

Dijkstra’s Algorithm is one of the most reliable and efficient shortest path algorithms for graphs with **non-negative weights**. Its versatility makes it suitable for a wide range of problem types — from basic shortest path queries to complex path validation problems.

---

**Pro Tip 🔥**  
> Always add `if (current.distance > dist[node]) continue;` when using a PriorityQueue to skip stale entries and avoid unnecessary processing.


## ✅ Dijkstra Limitations

-   **Only works on graphs with non-negative edge weights**
    
-   Cannot directly handle negative weights (use Bellman-Ford for that)
    

----------

## ✅ Why Not Early Return at Destination?

You can early return when you pop the destination from the queue **if you only care about its min distance**.  
But if you need **distances to all nodes** (e.g., for multi-query problems or shortest path reconstruction),  
**you must let Dijkstra run to completion**.

----------

## ✅ Time Complexity

-   Using a priority queue: **O(E log V)**  
    (Because each edge may cause a logV operation on the queue)
    

----------

## ✅ Final Tip

Always remember:  
👉 Multiple entries in PQ are normal  
👉 Always check `if (current.distance > dist[node]) continue;`  
👉 Never early-return unless your problem explicitly allows it

----------

