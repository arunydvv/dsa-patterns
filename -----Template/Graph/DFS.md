
# 📌 Depth-First Search (DFS) 

**DFS (Depth-First Search)** is a graph traversal algorithm that explores as far as possible along each branch before backtracking.  
It uses a **stack (explicit or implicit via recursion)** to track exploration paths.

DFS is ideal for problems where you need to:
- Visit all nodes in a connected component
- Detect cycles
- Traverse paths deeply before moving to neighbors

---

## ✅ Key Concepts & Invariants

| Concept                             | Explanation                                                                                  |
|:------------------------------------|:---------------------------------------------------------------------------------------------|
| Traversal Order                     | Depth-first — explores a path fully before backtracking                                       |
| Data Structure Used                 | **Recursion stack** (implicit) or **explicit stack**                                          |
| Suitable for                        | Connected components, cycle detection, topological sorting, path enumeration, tree traversals |
| Node revisitation                   | Mark nodes as visited to avoid infinite loops                                                 |
| Backtracking possible               | Yes — returns control to a previous node after exploring its neighbors                       |

---

## ✅ Standard DFS Code (Java)

### 📌 Recursive DFS

```java
import java.util.*;

public class DFSTemplate {
    void DFS(int node, boolean[] visited, List<List<Integer>> adj) {
        visited[node] = true;

        for (int neighbour : adj.get(node)) {
            if (!visited[neighbour]) {
                DFS(neighbour, visited, adj);
            }
        }
    }
}

```

### 📌 Iterative DFS (using Stack)

```java
import java.util.*;

public class DFSTemplateIterative {
    void DFS(int source, boolean[] visited, List<List<Integer>> adj) {
        Stack<Integer> stack = new Stack<>();
        stack.push(source);

        while (!stack.isEmpty()) {
            int node = stack.pop();

            if (visited[node]) continue;
            visited[node] = true;

            for (int neighbour : adj.get(node)) {
                if (!visited[neighbour]) {
                    stack.push(neighbour);
                }
            }
        }
    }
}

```

----------


## ✅ Use-Cases in Problems 🔥

| Problem Type                     | DFS Application                                                                 |
|:----------------------------------|:--------------------------------------------------------------------------------|
| **Finding connected components**  | Traverse all nodes reachable from a given node                                   |
| **Cycle detection in graphs**     | Detect cycles in directed or undirected graphs                                   |
| **Path enumeration problems**     | Explore all possible paths (like word search, maze paths)                        |
| **Topological sorting**           | Use DFS with post-order recording to get a valid topological order               |
| **Tree problems**                 | Subtree sums, Lowest Common Ancestor (LCA), diameter of tree using DFS           |

----------

## 📌 When to Use DFS?

✅ When you need to explore as deep as possible before backtracking  
✅ When finding connected components  
✅ When detecting cycles  
✅ When path enumeration is required  
✅ When solving tree-based problems

----------


## 📌 Related Algorithms

| Algorithm              | Use-Case                                                                |
|:----------------------|:------------------------------------------------------------------------|
| **BFS**                | When shortest path (in terms of steps) or level-wise traversal is needed |
| **Dijkstra**           | When shortest path with weighted edges is required                      |
| **Tarjan's Algorithm** | Strongly Connected Components (SCC) detection using DFS                 |
| **Kosaraju's Algorithm** | Another SCC detection technique via 2-pass DFS                         |


----------

## 📌 Example Problems

-   **LeetCode 200 — Number of Islands**
    
-   **LeetCode 694 — Number of Distinct Islands**
    
-   **LeetCode 695 — Max Area of Island**
    
-   **LeetCode 547 — Number of Provinces**
    
-   **CSES — Counting Rooms**
    
-   **Codeforces — Connected Components**
    

----------

## ✅ Summary

DFS is one of the most powerful and flexible graph traversal techniques, ideal for exploring connected components, cycle detection, path enumeration, and tree operations. Its recursive nature makes it a natural fit for problems where depth-first exploration is needed.

----------

## ✅ DFS Limitations

-   May cause **stack overflow** for very deep recursion (can use iterative DFS in such cases)
    
-   Not suitable for shortest path problems in weighted/unweighted graphs (use BFS/Dijkstra instead)
    

----------

## ✅ Time Complexity

-   **O(V + E)**  
    (V = number of vertices, E = number of edges)
    

----------

## ✅ Final Tip

Always remember:  
👉 DFS explores as deep as possible before backtracking  
👉 Recursion stack can overflow — iterative DFS is an alternative  
👉 Track visited nodes carefully to avoid infinite loops  
👉 Useful for trees, connected components, and cycle detection

----------

