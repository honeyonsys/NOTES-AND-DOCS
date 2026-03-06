# **F L O Y D - W A R S H A L L**  

---

## **Problem Statement**  
Given a **graph with weighted edges**, find the **shortest paths between all pairs of nodes**.  

Unlike **Dijkstra’s** and **Bellman-Ford**, which focus on a **single source**, **Floyd-Warshall** finds the shortest path **between every pair of vertices** in a **weighted graph** (including negative weights but not negative cycles).  

---

## **Real-World Example: Flight Route Optimization**  
Imagine you are managing an **airline system**, and you need to find the **shortest travel time** between every pair of cities.  
- Cities are **nodes**.  
- Flight routes are **edges with weights (time or cost)**.  
- The **Floyd-Warshall Algorithm** helps find the **fastest routes** between all cities.  

---

## **Solution Explanation**  
1. **Create a distance matrix** (2D array) where:  
   - \( \text{distance}[i][j] \) = weight of the edge between node \( i \) and \( j \).  
   - If no direct edge exists, set distance to **infinity (\(\infty\))**.  
   - Distance from a node to itself is **0**.  
2. **Iterate through all nodes as intermediate nodes** and update shortest paths:  
   - For each node \( k \), check if the path **i → k → j** is shorter than **i → j** directly.  
   - Update distance if a shorter path is found.  
3. **Detect negative weight cycles**: If **distance[i][i] < 0**, a negative cycle exists.  

---

## **Time Complexity**  
- **\( O(V^3) \) (Cubic complexity)**, where \( V \) is the number of vertices.  
- **Efficient for small to medium graphs** but **not for large graphs**.  

## **Space Complexity**  
- \( O(V^2) \) (Distance matrix storage).  

---

# **Java Code Implementation**
```java
import java.util.Arrays;

class FloydWarshall {
    final static int INF = 99999; // Representation of infinity

    public static void floydWarshall(int[][] graph) {
        int V = graph.length;
        int[][] dist = new int[V][V];

        // Initialize distance matrix with given graph
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                dist[i][j] = graph[i][j];
            }
        }

        // Updating distances using each vertex as an intermediate node
        for (int k = 0; k < V; k++) {
            for (int i = 0; i < V; i++) {
                for (int j = 0; j < V; j++) {
                    if (dist[i][k] != INF && dist[k][j] != INF && dist[i][k] + dist[k][j] < dist[i][j]) {
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }

        // Check for negative weight cycles
        for (int i = 0; i < V; i++) {
            if (dist[i][i] < 0) {
                System.out.println("Graph contains a negative weight cycle!");
                return;
            }
        }

        // Print shortest distance matrix
        printSolution(dist);
    }

    public static void printSolution(int[][] dist) {
        int V = dist.length;
        System.out.println("Shortest distances between every pair of vertices:");
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                if (dist[i][j] == INF)
                    System.out.print("INF ");
                else
                    System.out.print(dist[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int[][] graph = {
            {0, 3, INF, 5},
            {2, 0, INF, 4},
            {INF, 1, 0, INF},
            {INF, INF, 2, 0}
        };

        floydWarshall(graph);
    }
}
```

---

# **Why Use Floyd-Warshall Algorithm?**  
✅ **Finds shortest paths between all pairs of vertices**.  
✅ **Handles negative weights (but not negative cycles)**.  
✅ **Simpler implementation compared to Dijkstra's for multiple sources**.  
❌ **Not suitable for large graphs (due to \( O(V^3) \) complexity)**.  
