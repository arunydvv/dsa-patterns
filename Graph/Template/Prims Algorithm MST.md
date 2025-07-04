

# 📒 Prim’s Algorithm for Minimum Spanning Tree (MST)





Prim’s Algorithm is a **greedy algorithm** that builds the MST by:

-   Starting from any node.
    
-   At each step, picking the **minimum weight edge** that connects a new node to the growing MST.
    
-   Repeating this until all nodes are included in the MST.
    



## 📌 Core Idea:

Use a **PriorityQueue (Min-Heap)** to efficiently get the next smallest weight edge.

----------

## 📌 Standard Java Implementation (with PriorityQueue)

### ✅ Code:

```java
import java.util.*;

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

class Solution {
    static int spanningTree(int V, int E, List<List<int[]>> adj) {
        int sum = 0;
        PriorityQueue<Pair> pq = new PriorityQueue<>();
        pq.add(new Pair(0, 0));

        boolean[] inMST = new boolean[V];

        while (!pq.isEmpty()) {
            Pair current = pq.poll();
            int node = current.node;
            int distance = current.distance;

            if (inMST[node]) continue;
            inMST[node] = true;
            sum += distance;

            for (int[] next : adj.get(node)) {
                int neighbour = next[0];
                int nextWeight = next[1];

                if (!inMST[neighbour]) {
                    pq.add(new Pair(nextWeight, neighbour));
                }
            }
        }

        return sum;
    }
}

```

----------

## 📌 Time and Space Complexity

Operation

Complexity

**Time**

`O(E log V)`

**Space**

`O(V + E)`

**Why?**

-   Each edge can be pushed into the PriorityQueue.
    
-   PriorityQueue operations take `O(log V)` time.
    
-   Each node is processed once.
    

----------

## 📌 Input Graph Format

Use **Adjacency List** representation:

```java
List<List<int[]>> adj = new ArrayList<>();
for (int i = 0; i < V; i++) adj.add(new ArrayList<>());

adj.get(u).add(new int[]{v, weight});
adj.get(v).add(new int[]{u, weight});

```

----------

## 📌 Important Variants & Notes 🔥

### 1️⃣ Lazy Prim’s (Standard one you just saw)

-   Uses a `PriorityQueue<Pair>` and a `boolean[] inMST`.
    
-   No need to decrease keys — just add possible options to the queue.
    
-   Skip already visited nodes.
    

**Advantage**: Simple to implement.

----------

### 2️⃣ Eager Prim’s

-   Uses a **PriorityQueue (min-heap)**, but with an additional `key[]` array to track the current minimum weight to reach each vertex.
    
-   You update the key value when you find a better option.
    
-   Requires either:
    
    -   Custom decrease-key support in PriorityQueue (hard in Java)
        
    -   Or simulate via re-adding with updated key and skipping worse ones.
        

**Example C++ implementations usually prefer this.**

----------

### 3️⃣ Prim’s with Path Construction

-   Store parent information to reconstruct the actual MST edges.
    

```java
int[] parent = new int[V];
Arrays.fill(parent, -1);

```

And update:

```java
parent[neighbour] = node;

```

Then, later traverse `parent[]` to list MST edges.

----------

### 4️⃣ Disconnected Graphs (Multiple MSTs)

If the graph is disconnected:

-   Prim’s will only process one connected component.
    
-   If required to get total MST weight for all components:
    
    -   Run Prim’s repeatedly on unvisited nodes.
        






# 📑 Prim’s vs Kruskal’s Algorithm

A comparison of two classic greedy algorithms for finding the Minimum Spanning Tree (MST) of a connected, undirected, weighted graph.

---

## 📊 Comparison Table

| Feature                         | Prim’s Algorithm                                                | Kruskal’s Algorithm                                             |
|:--------------------------------|:---------------------------------------------------------------|:---------------------------------------------------------------|
| **Type**                        | Greedy                                                         | Greedy                                                         |
| **Approach**                    | Grows MST by adding the minimum weight edge from existing tree  | Grows MST by picking the smallest edge, avoiding cycles        |
| **Data Structure Used**         | Priority Queue / Min-Heap (for efficient edge selection)        | Disjoint Set (Union-Find) to detect and avoid cycles           |
| **Time Complexity**             | O(E log V) with Min-Heap + Adjacency List                       | O(E log E) (since E log E dominates sorting of edges)          |
| **Space Complexity**            | O(V + E)                                                       | O(V + E)                                                       |
| **Graph Representation**        | Adjacency List (preferred for sparse graphs)                    | Edge List                                                      |
| **Edge Selection**              | Chooses edge connecting a vertex inside the MST to one outside  | Chooses the overall smallest edge not forming a cycle          |
| **Starting Point**              | Starts from any arbitrary vertex                                | No specific starting point needed                              |
| **Cycle Detection**             | No explicit cycle check needed (safe selection ensured by PQ)   | Requires cycle detection via Disjoint Set                      |
| **Works on**                    | Connected, undirected, weighted graphs                          | Connected, undirected, weighted graphs                          |
| **Suitable For**                | Dense graphs                                                    | Sparse graphs                                                  |
| **Implementation Complexity**   | Slightly more complex due to priority queue handling             | Simpler due to sorting and Union-Find operations               |

---

## 📌 Notes

- **Prim’s Algorithm**
  - Best for dense graphs because it picks the cheapest edge from a set of connected nodes efficiently using a Priority Queue.
  - Often implemented with an adjacency list and a min-heap for optimal performance.

- **Kruskal’s Algorithm**
  - Works well for sparse graphs as it sorts all edges first.
  - Uses Union-Find (Disjoint Set Union) to detect cycles when adding edges to the MST.

---













## 📌 Key Interview Points ⭐

-   **Time Complexity**: `O(E log V)`
    
-   **Use PriorityQueue / Min-Heap for efficient edge selection**
    
-   Works for **connected undirected weighted graphs**
    
-   Better than Kruskal’s for **dense graphs**
    
-   If required MST edges: track `parent[]` array
    
-   Can be modified to work for disconnected graphs by restarting on unvisited nodes
    

----------

## 📌 Practice Problems

-   **GFG:** [Minimum Spanning Tree (Prim’s)](https://practice.geeksforgeeks.org/problems/minimum-spanning-tree/1)
    
-   **LeetCode:** No direct MST problem — but helpful in:
    
    -   [Connecting Cities With Minimum Cost](https://leetcode.com/problems/connecting-cities-with-minimum-cost/)
        
    -   [Optimize Water Distribution in a Village](https://leetcode.com/problems/optimize-water-distribution-in-a-village/)
        

----------

## 📌 Summary

✅ Prim’s is a classic MST algorithm ideal for **dense graphs** using **greedy selection** with a **min-priority queue**.  
✅ In Java, make sure your custom class (Pair) implements `Comparable` or use a custom `Comparator`.

----------

