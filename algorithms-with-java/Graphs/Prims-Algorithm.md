# **P R I M ' S**  

---

## **Problem Statement**  
Given a **weighted, connected, and undirected graph**, find a **Minimum Spanning Tree (MST)**.  

- A **spanning tree** connects all the nodes in the graph with the **minimum possible total edge weight**.  
- **Prim's Algorithm** is a **greedy algorithm** that grows the MST **one node at a time** by selecting the **minimum weight edge** that **connects a new node** to the tree.

---

## **Real-World Example: Laying Internet Cables**  
Imagine you are **laying fiber-optic cables** between cities.  
- Each **city** is a **node**.  
- Laying cables between two cities has a **cost** (edge weight).  
- You need to **connect all cities with the minimum total cost**.  
- **Prim’s Algorithm** helps find the **cheapest way** to connect all cities **without forming cycles**.

---

## **Solution Explanation**  
1. **Start with any node** and add it to the MST.  
2. **Find the smallest edge** that connects a new node to the MST.  
3. **Repeat until all nodes are included in the MST**.  

---

## **Time Complexity**  
- **\( O(V^2) \)** (with an adjacency matrix).  
- **\( O(E \log V) \)** (using a **priority queue**).  
- **Faster than Kruskal’s Algorithm** for **dense graphs**.

## **Space Complexity**  
- \( O(V) \) (to store MST).

---

# **Java Code Implementation**
```java
import java.util.*;

class PrimsAlgorithm {
    static class Edge implements Comparable<Edge> {
        int node, weight;
        Edge(int node, int weight) {
            this.node = node;
            this.weight = weight;
        }
        public int compareTo(Edge other) {
            return this.weight - other.weight;
        }
    }

    public static void primsMST(int[][] graph) {
        int V = graph.length;
        boolean[] inMST = new boolean[V]; // Track nodes in MST
        int[] minWeight = new int[V]; // Store min edge weight for each node
        int[] parent = new int[V]; // Store MST structure

        Arrays.fill(minWeight, Integer.MAX_VALUE);
        minWeight[0] = 0;
        parent[0] = -1; // Start from node 0

        PriorityQueue<Edge> pq = new PriorityQueue<>();
        pq.add(new Edge(0, 0));

        while (!pq.isEmpty()) {
            int u = pq.poll().node;
            inMST[u] = true;

            for (int v = 0; v < V; v++) {
                if (graph[u][v] != 0 && !inMST[v] && graph[u][v] < minWeight[v]) {
                    minWeight[v] = graph[u][v];
                    pq.add(new Edge(v, minWeight[v]));
                    parent[v] = u;
                }
            }
        }

        // Print MST
        System.out.println("Minimum Spanning Tree (MST):");
        for (int i = 1; i < V; i++) {
            System.out.println(parent[i] + " - " + i + " (" + graph[i][parent[i]] + ")");
        }
    }

    public static void main(String[] args) {
        int[][] graph = {
            {0, 2, 0, 6, 0},
            {2, 0, 3, 8, 5},
            {0, 3, 0, 0, 7},
            {6, 8, 0, 0, 9},
            {0, 5, 7, 9, 0}
        };

        primsMST(graph);
    }
}
```

---

# **Why Use Prim's Algorithm?**  
✅ **Guaranteed to give the optimal MST**.  
✅ **Efficient for dense graphs** (better than Kruskal’s).  
✅ **Can handle weighted graphs easily**.  
❌ **Not efficient for sparse graphs compared to Kruskal’s Algorithm**.  
