
## ✅ Floyd-Warshall in Java (Edges to All-Pairs Shortest Paths)

```java
import java.util.*;

public class FloydWarshallEdges {

    static final int INF = (int) 1e9;

    public static void floydWarshall(int n, int[][] edges) {
        int[][] dist = new int[n][n];

        // 1️⃣ Initialize distance matrix
        for (int i = 0; i < n; i++) {
            Arrays.fill(dist[i], INF);
            dist[i][i] = 0;
        }

        // 2️⃣ Populate initial distances from given edges
        for (int[] edge : edges) {
            int u = edge[0];
            int v = edge[1];
            int wt = edge[2];
            dist[u][v] = wt;
            // If undirected graph:
            // dist[v][u] = wt;
        }

        // 3️⃣ Run Floyd-Warshall
        for (int k = 0; k < n; k++) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    if (dist[i][k] < INF && dist[k][j] < INF) {
                        dist[i][j] = Math.min(dist[i][j], dist[i][k] + dist[k][j]);
                    }
                }
            }
        }

        // 4️⃣ Optional: Detect Negative Cycle
        for (int i = 0; i < n; i++) {
            if (dist[i][i] < 0) {
                System.out.println("Negative weight cycle detected.");
                return;
            }
        }

        // 5️⃣ Print shortest distances
        printSolution(dist, n);
    }

    public static void printSolution(int[][] dist, int n) {
        System.out.println("Shortest distances between every pair of vertices:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (dist[i][j] == INF)
                    System.out.print("INF ");
                else
                    System.out.print(dist[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n = 4;  // Number of vertices
        int[][] edges = {
            {0, 1, 5},
            {0, 3, 10},
            {1, 2, 3},
            {2, 3, 1}
        };

        floydWarshall(n, edges);
    }
}

```

----------

## 📌 Explanation

Step

Description

**1️⃣ Initialize dist[][]**

Set all distances to `INF`, and `0` for self-loops `dist[i][i]`

**2️⃣ Populate from edges**

For each edge `(u, v, wt)` set `dist[u][v] = wt`

**3️⃣ Core Floyd-Warshall**

Triple nested loop updating via intermediate vertices `k`

**4️⃣ Detect negative cycles**

If `dist[i][i] < 0` for any vertex

**5️⃣ Output result**

Print final distances

----------

## 📌 Notes:

-   Works for **directed** graphs; for undirected, just also set `dist[v][u] = wt`.
    
-   Handles graphs with **negative weights (no negative cycles)**.
    
-   Can be easily extended to **path reconstruction** with a `next[][]` matrix.
    

----------

## ✅ Summary:

-   No adjacency matrix assumption.
    
-   Clean edge list → dist[][] conversion.
    
-   Full Floyd-Warshall application.
    
-   Negative cycle detection.
    
-   O(V³) time, O(V²) space.
    

