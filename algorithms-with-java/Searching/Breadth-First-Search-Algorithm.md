# **B R E A D T H - F I R S T - S E A R C H (BFS)**  
## **Problem Statement**  
Given a **graph or tree**, traverse all the nodes using the **Breadth First Search (BFS)** algorithm.  

Unlike **Depth First Search (DFS)**, which explores **deep paths first**, BFS explores all nodes at the **current level** before moving to the next level. BFS is implemented using a **queue (FIFO - First In, First Out)**.  

---

## **Real-World Example: Finding the Shortest Path in a City**  
Imagine you are navigating a **city with interconnected roads**, and you want to find the **shortest path** to a destination.  

1. You start at the **current location (source node)**.  
2. You explore **all nearby roads (adjacent nodes)** first before moving further.  
3. Once you visit all **places at the current distance**, you move to the next level (places farther away).  
4. This ensures that the first time you reach a destination, it is via the **shortest path**.  

This **level-wise exploration** makes BFS ideal for **shortest path problems** in **unweighted graphs**.  

---

## **Solution Explanation**  
1. **Start from a given node** and mark it as **visited**.  
2. **Push it into a queue**.  
3. **While the queue is not empty**:  
   - Dequeue the front node.  
   - Visit all its **unvisited adjacent nodes** and enqueue them.  
4. Repeat until all nodes are visited.  

## **Time Complexity**  
- **Worst, Best & Average Case:** \(O(V + E)\), where \(V\) is the number of vertices and \(E\) is the number of edges.  

## **Space Complexity**  
- \(O(V)\) (for queue and visited nodes).  

---

# **Java Code Implementation**  
## **BFS for Graph (Using Queue - Iterative Approach)**  
```java
import java.util.*;

public class BFSGraph {
    static void bfs(Map<Integer, List<Integer>> graph, int start) {
        Queue<Integer> queue = new LinkedList<>();
        Set<Integer> visited = new HashSet<>();

        queue.add(start);
        visited.add(start);

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");

            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                if (!visited.contains(neighbor)) {
                    queue.add(neighbor);
                    visited.add(neighbor);
                }
            }
        }
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        System.out.println("BFS Traversal:");
        bfs(graph, 0);  // Start BFS from node 0
    }
}
```

---

## **BFS for Shortest Path in an Unweighted Graph**  
BFS can also be used to find the **shortest path** in an unweighted graph by keeping track of the distance from the source node.

```java
import java.util.*;

public class ShortestPathBFS {
    static int shortestPath(Map<Integer, List<Integer>> graph, int start, int target) {
        Queue<Integer> queue = new LinkedList<>();
        Map<Integer, Integer> distance = new HashMap<>();

        queue.add(start);
        distance.put(start, 0);

        while (!queue.isEmpty()) {
            int node = queue.poll();

            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                if (!distance.containsKey(neighbor)) {
                    queue.add(neighbor);
                    distance.put(neighbor, distance.get(node) + 1);

                    if (neighbor == target) {
                        return distance.get(neighbor);  // Found the shortest path
                    }
                }
            }
        }
        return -1;  // Target not reachable
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        int start = 0, target = 6;
        int result = shortestPath(graph, start, target);

        if (result != -1) {
            System.out.println("Shortest path from " + start + " to " + target + " is " + result);
        } else {
            System.out.println("No path found");
        }
    }
}
```

---

## **Why Use BFS?**
✅ **Finds the shortest path in an unweighted graph**.  
✅ **Best for level-wise exploration (e.g., social networks, mazes, web crawling)**.  
✅ **Guaranteed to visit each node at least once**.  
❌ **Uses more memory than DFS (queue storage)**.  
