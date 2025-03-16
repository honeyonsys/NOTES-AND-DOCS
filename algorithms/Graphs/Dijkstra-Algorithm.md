# **D I J K S T R A**  

---

## **Problem Statement**  
Given a **weighted graph** with **non-negative** edge weights, find the **shortest path** from a **starting node** to all other nodes in the graph.

Dijkstra’s Algorithm is a **greedy algorithm** that efficiently finds the **shortest path** from a **single source node** to all other nodes in a **graph**.

---

## **Real-World Example: Google Maps (Shortest Path Calculation)**  
Imagine you are using **Google Maps** to find the **shortest route** between two locations.  
- The locations are represented as **nodes** in a graph.  
- Roads connecting them have **weights (time/distance)**.  
- Dijkstra’s Algorithm helps find the **fastest/shortest route** to the destination.  

For example:  
If you are at **Point A** and want to reach **Point B**, the algorithm finds the **quickest path**, considering traffic, road distance, and speed limits.

---

## **Solution Explanation**  
1. **Initialize** the distances of all nodes as **infinity** (except the starting node, which is set to 0).  
2. Use a **priority queue (Min-Heap)** to always process the node with the **smallest distance**.  
3. For each node, **update the distances** of its adjacent nodes **if a shorter path is found**.  
4. Repeat until all nodes are processed.  
5. The result is the **shortest distance** from the source node to all other nodes.  

---

## **Time Complexity**  
- **Using Priority Queue (Min-Heap):** \( O((V + E) \log V) \)  
  - \( V \) = Number of vertices (nodes).  
  - \( E \) = Number of edges (connections).  

## **Space Complexity**  
- \( O(V + E) \) (for graph storage and distance tracking).  

---

# **Java Code Implementation (Using Priority Queue - Min-Heap)**
```java
import java.util.*;

class Dijkstra {
    static class Node {
        int vertex, weight;

        Node(int v, int w) {
            vertex = v;
            weight = w;
        }
    }

    public static void dijkstra(Map<Integer, List<Node>> graph, int source) {
        PriorityQueue<Node> pq = new PriorityQueue<>(Comparator.comparingInt(n -> n.weight));
        Map<Integer, Integer> distance = new HashMap<>();
        
        for (int node : graph.keySet()) {
            distance.put(node, Integer.MAX_VALUE);
        }
        distance.put(source, 0);

        pq.add(new Node(source, 0));

        while (!pq.isEmpty()) {
            Node current = pq.poll();
            int currentVertex = current.vertex;

            for (Node neighbor : graph.getOrDefault(currentVertex, new ArrayList<>())) {
                int newDist = distance.get(currentVertex) + neighbor.weight;

                if (newDist < distance.get(neighbor.vertex)) {
                    distance.put(neighbor.vertex, newDist);
                    pq.add(new Node(neighbor.vertex, newDist));
                }
            }
        }

        // Print shortest distances
        for (Map.Entry<Integer, Integer> entry : distance.entrySet()) {
            System.out.println("Distance from node " + source + " to node " + entry.getKey() + " is " + entry.getValue());
        }
    }

    public static void main(String[] args) {
        Map<Integer, List<Node>> graph = new HashMap<>();

        graph.put(0, Arrays.asList(new Node(1, 4), new Node(2, 1)));
        graph.put(1, Arrays.asList(new Node(3, 1)));
        graph.put(2, Arrays.asList(new Node(1, 2), new Node(3, 5)));
        graph.put(3, new ArrayList<>());

        int source = 0;
        dijkstra(graph, source);
    }
}
```

---

## **Why Use Dijkstra's Algorithm?**  
✅ **Finds the shortest path efficiently**.  
✅ **Works well for road networks, flight paths, internet routing**.  
✅ **Greedy strategy ensures optimal results for non-negative weights**.  
❌ **Does not work for graphs with negative edge weights (use Bellman-Ford instead).**  
