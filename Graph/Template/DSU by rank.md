
## 📌 What is DSU (Disjoint Set Union)?

A **Disjoint Set Union (Union-Find)** is a data structure that efficiently manages a collection of disjoint sets, allowing:

-   **Find(x)** → Get the leader (representative) of the set containing `x`.
    
-   **Union(x, y)** → Merge the two sets containing `x` and `y`.
    

----------

## 📌 Why DSU by Rank?

In **DSU by Rank**, we keep track of the **approximate depth (rank)** of each tree.  
When merging two trees, we attach the tree with **lower rank under the one with higher rank** to avoid increasing tree height unnecessarily.

This keeps the trees balanced and ensures efficient operations.

----------

## 📦 Key Components

Array

Purpose

`parent[]`

Stores the immediate parent of each node. If `parent[x] == x`, then `x` is the leader (root) of its component.

`rank[]`

Approximate depth of the tree rooted at each node. Used to decide how to merge two sets during a union.

----------

## 📌 Important Properties

-   **Union by Rank** ensures that the shallower tree is always attached under the deeper one.
    
-   **Path Compression** in `find` flattens the tree, pointing each node directly to its component leader.
    
-   Amortized Time Complexity: **O(α(N))** where `α` is the Inverse Ackermann function (practically constant for N ≤ 10⁹).
    

----------

## 📦 DSU by Rank Implementation in Java

```java
class DSU {
    int[] parent;
    int[] rank;

    // Constructor
    public DSU(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;  // Each node is its own parent initially
            rank[i] = 0;    // Rank (depth) is 0 initially
        }
    }

    // Find with path compression
    public int find(int x) {
        if (parent[x] != x)
            parent[x] = find(parent[x]);
        return parent[x];
    }

    // Union by Rank
    public void union(int x, int y) {
        int xp = find(x);
        int yp = find(y);
        if (xp == yp) return;

        // Attach the lower-rank tree under the higher-rank one
        if (rank[xp] < rank[yp]) {
            parent[xp] = yp;
        } else if (rank[yp] < rank[xp]) {
            parent[yp] = xp;
        } else {
            parent[yp] = xp;
            rank[xp]++;
        }
    }
}

```

----------

## 📌 Use Cases of DSU by Rank

-   Detecting cycles in undirected graphs
    
-   Kruskal’s Minimum Spanning Tree algorithm
    
-   Connected component tracking
    
-   Network connectivity problems
    
-   Dynamic connectivity queries (are `u` and `v` connected?)
    

----------

## 📦 Difference Between Size, Rank, and Parent

Term

Meaning

When Used

`parent[x]`

Immediate parent of `x`. If `parent[x] == x`, then `x` is the representative (leader) of its component.

Always

`rank[x]`

Approximate depth of the tree rooted at `x`.

Used in **DSU by Rank**

`size[x]`

Number of elements in the component whose leader is `x`.

Used in **DSU by Size**

----------

## 📌 DSU by Rank vs DSU by Size

Aspect

DSU by Rank

DSU by Size

Merge Decision

Attach lower-ranked tree under higher-ranked one

Attach smaller-sized tree under larger one

Extra Array

`rank[]`

`size[]`

Use Case

When you only need connectivity info

When you care about component sizes

Path Compression

Yes

Yes

Time Complexity

O(α(N))

O(α(N))

----------

## 📌 Example Problem Applications

-   **Kruskal’s Algorithm** (for MST)
    
-   **Redundant Connection** (LeetCode 684)
    
-   **Connected Components in Graph**
    
-   **Dynamic connectivity problems**
    

----------

## 📖 Summary

**DSU by Rank** is a balanced merging strategy for disjoint sets:

-   Keeps component trees shallow.
    
-   Reduces the time for `find` and `union` operations.
    
-   Can be combined with **path compression** for near-constant time operations.
    
-   Best when you care about **connectivity structure only** (not sizes).
    

----------

