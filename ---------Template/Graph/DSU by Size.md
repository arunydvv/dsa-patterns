

## 📌 What is DSU (Disjoint Set Union)?

A **Disjoint Set Union (Union-Find)** is a data structure that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It supports two primary operations efficiently:

-   **Find(x)** → Determine which subset an element belongs to.
    
-   **Union(x, y)** → Merge the subsets containing elements `x` and `y`.
    

----------

## 📌 Why DSU by Size?

In **DSU by Size**, when merging two components, we attach the smaller-sized set under the larger one to keep the tree shallow, improving the efficiency of future `find` operations.

----------

## 📦 Key Components

Array

Purpose

`parent[]`

Stores the immediate parent of each node. If `parent[x] == x`, then `x` is the leader (root) of its component.

`size[]`

Keeps track of the size of each component (number of elements in the set). Used to attach the smaller tree under the bigger one.

----------

## 📌 Important Properties

-   **Union by Size** ensures that smaller trees attach under larger trees, reducing tree height and making operations faster.
    
-   **Path Compression** in `find` flattens the tree structure by making each node directly point to the root, improving time complexity.
    
-   Amortized Time Complexity: **O(α(N))** where `α` is the Inverse Ackermann function (practically constant for N ≤ 10⁹).
    

----------

## 📦 DSU by Size Implementation in Java

```java
class DSU {
    int[] parent;
    int[] size;

    // Constructor
    public DSU(int n) {
        parent = new int[n];
        size = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;  // Each node is its own parent initially
            size[i] = 1;    // Size of each component is 1 initially
        }
    }

    // Find with path compression
    public int find(int x) {
        if (parent[x] != x)
            parent[x] = find(parent[x]);
        return parent[x];
    }

    // Union by Size
    public void union(int x, int y) {
        int xp = find(x);
        int yp = find(y);
        if (xp == yp) return;

        // Attach smaller component under larger one
        if (size[xp] < size[yp]) {
            parent[xp] = yp;
            size[yp] += size[xp];
        } else {
            parent[yp] = xp;
            size[xp] += size[yp];
        }
    }

    // Get size of component containing x
    public int getSize(int x) {
        return size[find(x)];
    }
}

```

----------

## 📌 Use Cases of DSU

-   Detecting cycles in an undirected graph
    
-   Kruskal’s Minimum Spanning Tree algorithm
    
-   Connected component tracking
    
-   Percolation models
    
-   Image segmentation
    
-   Network connectivity problems
    
-   Social network grouping
    
-   Island problems in grids (like LeetCode 827 — Making a Large Island)
    

----------

## 📦 Difference Between Size, Rank, and Parent

Term

Meaning

When Used

`parent[x]`

Immediate parent of `x`. If `parent[x] == x`, then `x` is the representative (leader) of its component.

Always

`size[x]`

Number of elements in the component whose leader is `x`.

Used in **DSU by Size**

`rank[x]`

Upper bound on the height of the tree rooted at `x`.

Used in **DSU by Rank**

----------

## 📌 DSU by Size vs DSU by Rank

Aspect

DSU by Size

DSU by Rank

Merge Decision

Attach smaller-sized tree under larger one

Attach lower-ranked tree under higher-ranked one

Extra Array

`size[]`

`rank[]`

Use Case

When you care about component sizes

When you only need connectivity info

Path Compression

Yes

Yes

Time Complexity

O(α(N))

O(α(N))

----------

## 📌 Example Problem Applications

-   **Making a Large Island** (LeetCode 827)
    
-   **Number of Provinces** (LeetCode 547)
    
-   **Accounts Merge** (LeetCode 721)
    
-   **Redundant Connection** (LeetCode 684)
    
-   **Connected Components in Graph**
    

----------

## 📖 Summary

**DSU by Size** is a powerful optimization technique that:

-   Keeps component trees shallow.
    
-   Reduces the time for `find` and `union` operations.
    
-   Can be combined with **path compression** for near-constant time operations.
    
-   Is very useful in problems involving grouping, connectivity, and dynamic merging.
    

----------

