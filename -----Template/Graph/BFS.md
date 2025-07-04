
# 📌 Breadth-First Search (BFS) 



**BFS (Breadth-First Search)** is a graph traversal algorithm that explores vertices in the order of their distance (in terms of number of edges) from the source vertex, visiting all neighbors level-by-level using a **queue (FIFO)**.

It works for both:
- **Unweighted graphs**
- **Graphs where edge weight is uniform (like weight = 1)**

---

## ✅ Key Concepts & Invariants

| Concept                             | Explanation                                                                                  |
|:------------------------------------|:---------------------------------------------------------------------------------------------|
| Traversal Order                     | Level by level — visiting all neighbors of a node before moving to the next level             |
| Data Structure Used                 | Queue (FIFO)                                                                                  |
| When is a node’s distance finalized?| When it is first dequeued from the queue — BFS ensures this is its shortest path length       |
| Suitable for                        | Unweighted graphs, uniform weight graphs (weight = 1), shortest path in grids, connected components |

---

## ✅ Standard BFS Code (Java)

```java
import java.util.*;

public class BFSTemplate {
    void BFS(int source, int[] dist, List<List<Integer>> adj) {
        Queue<Integer> q = new LinkedList<>();
        q.add(source);
        dist[source] = 0;

        while (!q.isEmpty()) {
            int node = q.poll();

            for (int neighbour : adj.get(node)) {
                if (dist[neighbour] == -1) {  // unvisited
                    dist[neighbour] = dist[node] + 1;
                    q.add(neighbour);
                }
            }
        }
    }
}

```

-   Initialize `dist[]` array with `-1` or `1e9` to represent unvisited nodes.
    
-   BFS automatically guarantees the first time you visit a node, it's through the shortest possible path (in terms of number of edges).
    

----------


## ✅ Use-Cases in Problems 🔥

| Problem Type                        | BFS Application                                                                                 |
|:------------------------------------|:------------------------------------------------------------------------------------------------|
| **Shortest path in unweighted graphs** | Classic application for pathfinding when all edges have equal weight                              |
| **Shortest path in grids**            | Used in 2D/3D grid problems to find shortest path (like maze solving, flood-fill, zombie spread)  |
| **Finding connected components**     | Identify separate groups of connected nodes                                                       |
| **Minimum steps to convert/transform** | When operations can be modeled as graph transitions (e.g., word ladder, number transformations)   |
| **Check for bipartite graph**         | Use BFS with a coloring technique to verify if a graph can be two-colored                         |


----------

## 📌 When to Use BFS?

✅ When the graph is **unweighted**  
✅ When edge weights are **equal (like 0-1 BFS)**  
✅ When performing **level-order or breadth-first traversal**  
✅ When you need to compute **minimum number of moves/steps**

----------


## 📌 Related Algorithms

| Algorithm      | Use-Case                                                   |
|:---------------|:-----------------------------------------------------------|
| **Dijkstra**    | When edge weights are **positive and non-uniform**          |
| **0-1 BFS**     | When edge weights are either **0 or 1**                     |
| **DFS**         | For **depth-based problems** like cycle detection, path enumeration |




## 📌 Example Problems

-   **LeetCode 1091 — Shortest Path in Binary Matrix**
    
-   **LeetCode 752 — Open the Lock**
    
-   **LeetCode 286 — Walls and Gates**
    
-   **CSES — Building Roads**
    
-   **Codeforces — Maze Escape**
    

----------

## ✅ Summary

BFS is a fundamental graph traversal technique, ideal for solving shortest path problems in unweighted or equally weighted graphs. Its simplicity and reliability make it a staple tool for competitive programming, interview preparation, and real-world graph modeling problems.

----------

## ✅ BFS Limitations

-   Cannot handle **weighted graphs with non-uniform weights** (use Dijkstra or Bellman-Ford instead)
    
-   BFS explores all neighbors uniformly, so not suitable when weights matter.
    

----------

## ✅ Time Complexity

-   **O(V + E)**  
    (V = number of vertices, E = number of edges)
    

----------

## ✅ Final Tip

Always remember:  
👉 BFS guarantees shortest distance (in number of edges) in unweighted or equally weighted graphs  
👉 For shortest path in weighted graphs — prefer Dijkstra or other variants  
👉 Use a distance array or visited array to track progress

----------

