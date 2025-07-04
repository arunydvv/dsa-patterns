
# 📒 Kruskal’s Algorithm for Minimum Spanning Tree (MST)


Kruskal’s Algorithm is a **greedy algorithm** that:

-   Sorts all the edges by weight.
    
-   Adds the next smallest edge to the MST if it doesn’t form a cycle.
    
-   Repeats until **V-1 edges** are added (for a connected graph with `V` vertices).


## 📌 Core Idea:

Uses a **Disjoint Set Union (DSU) / Union-Find** data structure to detect cycles efficiently.

----------

## 📌 Standard Java Implementation (with DSU)

### ✅ Code:

```java
import java.util.*;

class Edge implements Comparable<Edge> {
    int u, v, weight;
    Edge(int u, int v, int w) {
        this.u = u;
        this.v = v;
        this.weight = w;
    }

    @Override
    public int compareTo(Edge other) {
        return this.weight - other.weight;
    }
}

class DSU {
    int[] parent, rank;
    DSU(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) parent[i] = i;
    }

    int find(int x) {
        if (x != parent[x])
            parent[x] = find(parent[x]);
        return parent[x];
    }

    void union(int x, int y) {
        int px = find(x);
        int py = find(y);
        if (px == py) return;

        if (rank[px] < rank[py]) parent[px] = py;
        else if (rank[py] < rank[px]) parent[py] = px;
        else {
            parent[py] = px;
            rank[px]++;
        }
    }
}

class Solution {
    static int kruskalMST(int V, List<Edge> edges) {
        Collections.sort(edges); // Sort by weight
        DSU dsu = new DSU(V);
        int mstWeight = 0;

        for (Edge e : edges) {
            if (dsu.find(e.u) != dsu.find(e.v)) {
                dsu.union(e.u, e.v);
                mstWeight += e.weight;
            }
        }

        return mstWeight;
    }
}

```

----------

## 📌 Time and Space Complexity

Operation

Complexity

**Time**

`O(E log E)`

**Space**

`O(V + E)`

**Why?**

-   Sorting edges takes `O(E log E)`
    
-   DSU operations (`find` and `union`) take `O(α(V)) ≈ O(1)` on average per operation (α is inverse Ackermann function)
    

----------

## 📌 Input Graph Format

Use **Edge List** representation:

```java
List<Edge> edges = new ArrayList<>();
edges.add(new Edge(u, v, weight));

```

----------

## 📌 Important Variants & Notes 🔥

### 1️⃣ Kruskal’s With Path Construction

-   Maintain a `List<Edge>` to store MST edges while adding them.
    
-   Useful when you need to print actual MST edges.
    

### 2️⃣ Disconnected Graphs (Multiple MSTs)

-   If the graph is disconnected:
    
    -   Kruskal’s naturally handles this.
        
    -   Can be modified to stop when **number of edges = V-1** or just continue if asked for total weight of all MSTs (in all components).
        

### 3️⃣ Optimized DSU with Union By Rank & Path Compression

-   Current implementation already includes these:
    
    -   **Path compression** during `find`
        
    -   **Union by rank** during `union`
        



## 📌 Key Interview Points ⭐

-   **Time Complexity**: `O(E log E)`
    
-   Uses **DSU (Disjoint Set Union)** for efficient cycle detection.
    
-   Works for **connected and disconnected** undirected weighted graphs.
    
-   Better for **sparse graphs**
    
-   Track actual MST edges if asked.
    
-   Can find MST cost for disconnected graphs too.
    

----------

## 📌 Practice Problems

-   **GFG:** [Minimum Spanning Tree (Kruskal’s)](https://practice.geeksforgeeks.org/problems/minimum-spanning-tree/1)
    
-   **LeetCode:** No direct problem but applicable for:
    
    -   [Optimize Water Distribution in a Village](https://leetcode.com/problems/optimize-water-distribution-in-a-village/)
        
    -   [Connecting Cities With Minimum Cost](https://leetcode.com/problems/connecting-cities-with-minimum-cost/)
        

----------

## 📌 Summary

✅ Kruskal’s is a greedy MST algorithm ideal for **sparse graphs** using **edge sorting** and **cycle detection via DSU**.  
✅ In Java, use a custom class (`Edge`) with `Comparable` for sorting.

----------



