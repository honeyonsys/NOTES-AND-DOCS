# **B E L L M A N - F O R D**  

---

## **Problem Statement**  
Given a **weighted graph** (which can have **negative weights**), find the **shortest path** from a **single source node** to all other nodes.

Unlike **Dijkstra’s Algorithm**, which only works with **non-negative weights**, **Bellman-Ford** can handle **negative weights** and detect **negative weight cycles**.

---

## **Real-World Example: Currency Exchange (Arbitrage Detection)**  
Imagine you are trading **currencies**, and different **exchange rates** are given.  
- A **negative cycle** in the exchange rate graph means you can keep exchanging **currencies infinitely** and make unlimited profit.  
- The **Bellman-Ford Algorithm** helps detect such **negative cycles**, preventing unfair profit opportunities in financial markets.

---

## **Solution Explanation**  
1. **Initialize** distances of all nodes as **infinity** except the source (which is set to 0).  
2. **Relax all edges** \( V-1 \) times (where \( V \) is the number of vertices).  
   - This means checking all edges and **updating distances** if a shorter path is found.  
3. **Detect negative weight cycles** by checking if an edge can still be relaxed after \( V-1 \) iterations.  
   - If yes, there is a **negative weight cycle** in the graph.

---

## **Time Complexity**  
- **Worst Case:** \( O(VE) \), where \( V \) = number of vertices and \( E \) = number of edges.  
- **Slower than Dijkstra’s Algorithm** but works with **negative weights**.

## **Space Complexity**  
- \( O(V) \) (for storing distances).  

---

# **Java Code Implementation**
```java
import java.util.*;

class BellmanFord {
    static class Edge {
        int src, dest, weight;

        Edge(int s, int d, int w) {
            src = s;
            dest = d;
            weight = w;
        }
    }

    public static void bellmanFord(List<Edge> edges, int V, int source) {
        int[] distance = new int[V];
        Arrays.fill(distance, Integer.MAX_VALUE);
        distance[source] = 0;

        // Relax all edges V-1 times
        for (int i = 1; i < V; i++) {
            for (Edge edge : edges) {
                if (distance[edge.src] != Integer.MAX_VALUE &&
                        distance[edge.src] + edge.weight < distance[edge.dest]) {
                    distance[edge.dest] = distance[edge.src] + edge.weight;
                }
            }
        }

        // Check for negative weight cycles
        for (Edge edge : edges) {
            if (distance[edge.src] != Integer.MAX_VALUE &&
                    distance[edge.src] + edge.weight < distance[edge.dest]) {
                System.out.println("Graph contains a negative weight cycle!");
                return;
            }
        }

        // Print shortest distances
        for (int i = 0; i < V; i++) {
            System.out.println("Distance from node " + source + " to node " + i + " is " + distance[i]);
        }
    }

    public static void main(String[] args) {
        int V = 5;  // Number of vertices
        List<Edge> edges = new ArrayList<>();

        edges.add(new Edge(0, 1, -1));
        edges.add(new Edge(0, 2, 4));
        edges.add(new Edge(1, 2, 3));
        edges.add(new Edge(1, 3, 2));
        edges.add(new Edge(1, 4, 2));
        edges.add(new Edge(3, 2, 5));
        edges.add(new Edge(3, 1, 1));
        edges.add(new Edge(4, 3, -3));

        int source = 0;
        bellmanFord(edges, V, source);
    }
}
```

---

# **Why Use Bellman-Ford Algorithm?**  
✅ **Works with negative weight edges** (Dijkstra doesn’t).  
✅ **Detects negative weight cycles**.  
✅ **Simpler logic than Dijkstra (but slower)**.  
❌ **Not efficient for large graphs (slower than Dijkstra’s Algorithm)**.  
