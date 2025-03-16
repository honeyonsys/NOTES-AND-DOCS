# **K R U S K A L ' S**  

---

## **Problem Statement**  
Given a **weighted, connected, and undirected graph**, find the **Minimum Spanning Tree (MST)**.  

- A **spanning tree** connects all the nodes in the graph with the **minimum possible total edge weight**.  
- **Kruskal's Algorithm** is a **greedy algorithm** that sorts all edges by weight and picks the **smallest edges first**, ensuring no **cycles** are formed.

---

## **Real-World Example: Building Roads Between Cities**  
Imagine you are **constructing roads** to connect cities:  
- Each **city** is a **node**.  
- Each **road** has a **cost** (edge weight).  
- You need to **connect all cities at the lowest cost** while ensuring **no city is left unconnected**.  
- **Kruskal’s Algorithm** helps find the **cheapest road network**.

---

## **Solution Explanation**  
1. **Sort all edges by weight (ascending order).**  
2. **Initialize an empty MST.**  
3. **Pick the smallest edge** that **does not form a cycle**.  
4. **Use the Union-Find (Disjoint Set) data structure** to check cycles efficiently.  
5. **Repeat until MST contains \( V-1 \) edges (where \( V \) is the number of vertices).**

---

## **Time Complexity**  
- **\( O(E \log E) \)** (Sorting edges takes \( O(E \log E) \), and Union-Find operations take \( O(E \log V) \)).  
- **Better than Prim’s Algorithm** for **sparse graphs**.  

## **Space Complexity**  
- \( O(V + E) \) (to store edges and Union-Find data structure).  

---

# **Java Code Implementation**
```java
import java.util.*;

class KruskalsAlgorithm {
    static class Edge implements Comparable<Edge> {
        int src, dest, weight;
        Edge(int src, int dest, int weight) {
            this.src = src;
            this.dest = dest;
            this.weight = weight;
        }
        public int compareTo(Edge other) {
            return this.weight - other.weight;
        }
    }

    static class DisjointSet {
        int[] parent, rank;

        DisjointSet(int n) {
            parent = new int[n];
            rank = new int[n];
            for (int i = 0; i < n; i++) parent[i] = i;
        }

        int find(int v) {
            if (parent[v] != v)
                parent[v] = find(parent[v]); // Path compression
            return parent[v];
        }

        void union(int a, int b) {
            int rootA = find(a);
            int rootB = find(b);
            if (rootA != rootB) {
                if (rank[rootA] > rank[rootB])
                    parent[rootB] = rootA;
                else if (rank[rootA] < rank[rootB])
                    parent[rootA] = rootB;
                else {
                    parent[rootB] = rootA;
                    rank[rootA]++;
                }
            }
        }
    }

    public static void kruskalMST(int[][] graph) {
        int V = graph.length;
        List<Edge> edges = new ArrayList<>();

        // Convert adjacency matrix to edge list
        for (int i = 0; i < V; i++) {
            for (int j = i + 1; j < V; j++) {
                if (graph[i][j] != 0) {
                    edges.add(new Edge(i, j, graph[i][j]));
                }
            }
        }

        // Sort edges by weight
        Collections.sort(edges);

        DisjointSet ds = new DisjointSet(V);
        List<Edge> mst = new ArrayList<>();

        for (Edge edge : edges) {
            if (ds.find(edge.src) != ds.find(edge.dest)) { // Avoid cycle
                ds.union(edge.src, edge.dest);
                mst.add(edge);
                if (mst.size() == V - 1) break;
            }
        }

        // Print MST
        System.out.println("Minimum Spanning Tree (MST):");
        for (Edge edge : mst) {
            System.out.println(edge.src + " - " + edge.dest + " (" + edge.weight + ")");
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

        kruskalMST(graph);
    }
}
```

---

## **Why Use Kruskal's Algorithm?**  
✅ **Guaranteed to give the optimal MST**.  
✅ **Efficient for sparse graphs**.  
✅ **Uses a simple approach (edge sorting + Union-Find for cycle detection)**.  
❌ **Less efficient than Prim’s Algorithm for dense graphs**.  
