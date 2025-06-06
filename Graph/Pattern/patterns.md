
## 📚 Graph Algorithms and Patterns

### 1. **Graph Traversal**

-   **Breadth-First Search (BFS)**: Used for shortest path in unweighted graphs, level-order traversal.
    
    -   _Representative Problem_: [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)
        
-   **Depth-First Search (DFS)**: Used for path finding, cycle detection, topological sorting.
    
    -   _Representative Problem_: [Number of Islands](https://leetcode.com/problems/number-of-islands/)
        

### 2. **Cycle Detection**

-   **Undirected Graphs**: Using DFS or Union-Find.
    
    -   _Representative Problem_: [Detect Cycle in an Undirected Graph](https://www.geeksforgeeks.org/detect-cycle-undirected-graph/)([raahulsaxena.github.io](https://raahulsaxena.github.io/posts/2024/08/graph-problems-guide/?utm_source=chatgpt.com "Graphs: A Comprehensive Guide - Rahul Saxena"))
        
-   **Directed Graphs**: Using DFS with recursion stack or coloring method.
    
    -   _Representative Problem_: [Course Schedule](https://leetcode.com/problems/course-schedule/)
        

### 3. **Shortest Path Algorithms**

-   **Dijkstra's Algorithm**: For graphs with non-negative weights.
    
    -   _Representative Problem_: [Network Delay Time](https://leetcode.com/problems/network-delay-time/)
        
-   **Bellman-Ford Algorithm**: Handles negative weights.
    
    -   _Representative Problem_: [Bellman-Ford Algorithm](https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/)
        
-   **Floyd-Warshall Algorithm**: All-pairs shortest paths.
    
    -   _Representative Problem_: [Floyd Warshall Algorithm](https://www.geeksforgeeks.org/floyd-warshall-algorithm-dp-16/)
        

### 4. **Minimum Spanning Tree (MST)**

-   **Kruskal's Algorithm**: Greedy approach using Union-Find.
    
    -   _Representative Problem_: [Kruskal's Algorithm](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)
        
-   **Prim's Algorithm**: Greedy approach using priority queue.
    
    -   _Representative Problem_: [Prim's Algorithm](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/)
        

### 5. **Disjoint Set Union (Union-Find)**

-   Used for tracking connected components, cycle detection.
    
    -   _Representative Problem_: [Number of Connected Components in an Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
        

### 6. **Topological Sorting**

-   Linear ordering of vertices in a DAG.
    
    -   _Representative Problem_: [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
        

### 7. **Strongly Connected Components (SCC)**

-   **Kosaraju's Algorithm**: Two-pass DFS.
    
-   **Tarjan's Algorithm**: Single-pass DFS with low-link values.
    
    -   _Representative Problem_: [Strongly Connected Components](https://www.geeksforgeeks.org/strongly-connected-components/)
        

### 8. **Eulerian and Hamiltonian Paths**

-   **Eulerian Path**: Visits every edge exactly once.
    
    -   _Representative Problem_: [Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)
        
-   **Hamiltonian Path**: Visits every vertex exactly once.
    
    -   _Representative Problem_: [Hamiltonian Path](https://www.geeksforgeeks.org/hamiltonian-path-using-dynamic-programming/)
        

### 9. **Graph Coloring**

-   Assigning colors to vertices so that no two adjacent vertices share the same color.
    
    -   _Representative Problem_: [Graph Coloring](https://www.geeksforgeeks.org/graph-coloring-applications/)
        

### 10. **Bipartite Graph Check**

-   Determines if a graph's vertices can be divided into two sets with no internal edges.
    
    -   _Representative Problem_: [Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)
        

### 11. **Network Flow**

-   **Ford-Fulkerson Method**: Computes maximum flow in a flow network.
    
    -   _Representative Problem_: [Maximum Bipartite Matching](https://www.geeksforgeeks.org/maximum-bipartite-matching/)
        
-   **Edmonds-Karp Algorithm**: BFS-based implementation of Ford-Fulkerson.
    
    -   _Representative Problem_: [Edmonds-Karp Algorithm](https://www.geeksforgeeks.org/edmonds-karp-algorithm-for-maximum-flow-problem/)
        

### 12. **Articulation Points and Bridges**

-   Identifying critical nodes and edges whose removal increases the number of connected components.
    
    -   _Representative Problem_: [Articulation Points (or Cut Vertices) in a Graph](https://www.geeksforgeeks.org/articulation-points-or-cut-vertices-in-a-graph/)
        

----------

For a more exhaustive list, including over 100 graph algorithms and techniques, you can refer to the following resource:

-   [100+ Graph Algorithms and Techniques](https://iq.opengenus.org/list-of-graph-algorithms/)
    

