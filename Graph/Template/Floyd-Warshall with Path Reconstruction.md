

## ✅ Floyd-Warshall with Path Reconstruction (Java)

```java
import java.util.*;

public class FloydWarshallWithPath {
    static final int INF = (int)1e9;

    public static void floydWarshall(int[][] graph, int V) {
        int[][] dist = new int[V][V];
        int[][] next = new int[V][V];

        // Initialize distance and next matrices
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                dist[i][j] = graph[i][j];
                if (graph[i][j] != INF && i != j)
                    next[i][j] = j;
                else
                    next[i][j] = -1;
            }
        }

        // Core Floyd-Warshall with path recording
        for (int k = 0; k < V; k++) {
            for (int i = 0; i < V; i++) {
                for (int j = 0; j < V; j++) {
                    if (dist[i][k] < INF && dist[k][j] < INF) {
                        if (dist[i][j] > dist[i][k] + dist[k][j]) {
                            dist[i][j] = dist[i][k] + dist[k][j];
                            next[i][j] = next[i][k];
                        }
                    }
                }
            }
        }

        // Detect negative cycles
        for (int i = 0; i < V; i++) {
            if (dist[i][i] < 0) {
                System.out.println("Negative cycle detected");
                return;
            }
        }

        // Print shortest distances
        printSolution(dist, V);

        // Example: reconstruct path from 0 to 3
        System.out.print("Path from 0 to 3: ");
        List<Integer> path = reconstructPath(0, 3, next);
        if (path.isEmpty())
            System.out.println("No path");
        else
            System.out.println(path);
    }

    // Method to reconstruct path from u to v using next matrix
    public static List<Integer> reconstructPath(int u, int v, int[][] next) {
        List<Integer> path = new ArrayList<>();
        if (next[u][v] == -1) return path; // no path

        path.add(u);
        while (u != v) {
            u = next[u][v];
            path.add(u);
        }
        return path;
    }

    public static void printSolution(int[][] dist, int V) {
        System.out.println("Shortest distances between every pair of vertices:");
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                if (dist[i][j] == INF)
                    System.out.print("INF ");
                else
                    System.out.print(dist[i][j] + "   ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int V = 4;
        int[][] graph = {
            {0,   5,  INF, 10},
            {INF, 0,   3,  INF},
            {INF, INF, 0,   1},
            {INF, INF, INF, 0}
        };

        floydWarshall(graph, V);
    }
}

```

----------

## ✅ Explanation:

-   **`dist[i][j]`** → shortest distance from `i` to `j`
    
-   **`next[i][j]`** → next node on the shortest path from `i` to `j`
    
-   After the algorithm runs:
    
    -   If `next[u][v] == -1` → no path exists
        
    -   Else you can reconstruct the path by following `next[u][v], next[next[u][v]][v], ...` until you reach `v`.
        

----------

## ✅ Sample Output:

```
Shortest distances between every pair of vertices:
0   5   8   9   
INF 0   3   4   
INF INF 0   1   
INF INF INF 0   

Path from 0 to 3: [0, 1, 2, 3]

```

----------

## ✅ Time and Space Complexity:

-   **Time:** O(V³)
    
-   **Space:** O(V²) for both `dist` and `next` matrices
    

