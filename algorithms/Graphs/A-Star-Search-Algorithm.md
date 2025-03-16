# **A * ( A - S t a r ) - S e a r c h - A l g o r i t h m**  

---

## **Problem Statement**  
Given a **graph with weighted edges**, find the **shortest path** from a **start node** to a **goal node**.  

- **A* (A-Star) Search Algorithm** is an **informed search algorithm** that finds the optimal path efficiently.  
- It combines **Dijkstra’s Algorithm (cost-based search)** and **Greedy Best-First Search (heuristic-based search)** to minimize total cost.  

---

## **Real-World Example: Google Maps Navigation**  
Imagine you are using **Google Maps** to find the shortest route from **home to office**.  
- The **roads** are **edges**.  
- The **locations** (intersections) are **nodes**.  
- Each road has a **travel cost** (distance or time).  
- You want the **fastest route** considering both the **distance traveled so far (g-cost)** and the **estimated distance left (h-cost heuristic)**.  
- **A* Algorithm** helps find the most efficient route.

---

## **Solution Explanation**  
1. **Initialize two sets**:  
   - **Open Set** (nodes to explore).  
   - **Closed Set** (nodes already explored).  
2. **Set the cost of the start node** to **0**.  
3. **Pick the node with the lowest \( f \)-cost** (where \( f = g + h \)):  
   - \( g \) = cost from start node to current node.  
   - \( h \) = estimated heuristic cost from current node to goal.  
4. **Expand the node’s neighbors**, updating their costs if a shorter path is found.  
5. **Repeat until the goal node is reached**.  

---

## **Time Complexity**  
- **Worst case:** \( O(E) \) (similar to Dijkstra’s, depends on heuristic function).  
- **Best case:** Much faster if the heuristic is accurate.  

## **Space Complexity**  
- \( O(V) \) (stores all nodes in memory).  

---

# **Java Code Implementation**
```java
import java.util.*;

class AStarSearch {
    static class Node implements Comparable<Node> {
        int id, gCost, hCost, fCost;
        Node parent;

        Node(int id, int gCost, int hCost) {
            this.id = id;
            this.gCost = gCost;
            this.hCost = hCost;
            this.fCost = gCost + hCost;
            this.parent = null;
        }

        public int compareTo(Node other) {
            return this.fCost - other.fCost;
        }
    }

    public static void aStar(int[][] graph, int[] heuristic, int start, int goal) {
        int V = graph.length;
        PriorityQueue<Node> openSet = new PriorityQueue<>();
        HashSet<Integer> closedSet = new HashSet<>();
        Map<Integer, Node> nodeMap = new HashMap<>();

        Node startNode = new Node(start, 0, heuristic[start]);
        openSet.add(startNode);
        nodeMap.put(start, startNode);

        while (!openSet.isEmpty()) {
            Node current = openSet.poll();
            if (current.id == goal) {
                printPath(current);
                return;
            }

            closedSet.add(current.id);

            for (int neighbor = 0; neighbor < V; neighbor++) {
                if (graph[current.id][neighbor] == 0 || closedSet.contains(neighbor)) continue;

                int newGCost = current.gCost + graph[current.id][neighbor];
                if (!nodeMap.containsKey(neighbor) || newGCost < nodeMap.get(neighbor).gCost) {
                    Node neighborNode = new Node(neighbor, newGCost, heuristic[neighbor]);
                    neighborNode.parent = current;
                    nodeMap.put(neighbor, neighborNode);
                    openSet.add(neighborNode);
                }
            }
        }

        System.out.println("Path not found!");
    }

    private static void printPath(Node node) {
        List<Integer> path = new ArrayList<>();
        while (node != null) {
            path.add(node.id);
            node = node.parent;
        }
        Collections.reverse(path);
        System.out.println("Shortest Path: " + path);
    }

    public static void main(String[] args) {
        int[][] graph = {
            {0, 4, 0, 0, 0, 0, 0, 8, 0},
            {4, 0, 8, 0, 0, 0, 0, 11, 0},
            {0, 8, 0, 7, 0, 4, 0, 0, 2},
            {0, 0, 7, 0, 9, 14, 0, 0, 0},
            {0, 0, 0, 9, 0, 10, 0, 0, 0},
            {0, 0, 4, 14, 10, 0, 2, 0, 0},
            {0, 0, 0, 0, 0, 2, 0, 1, 6},
            {8, 11, 0, 0, 0, 0, 1, 0, 7},
            {0, 0, 2, 0, 0, 0, 6, 7, 0}
        };

        int[] heuristic = {7, 6, 2, 1, 0, 3, 2, 4, 5}; // Estimated heuristic cost to goal
        int start = 0, goal = 4;
        
        aStar(graph, heuristic, start, goal);
    }
}
```

---

## **Why Use A* Algorithm?**  
✅ **Guaranteed to find the shortest path (if heuristic is admissible and consistent).**  
✅ **Faster than Dijkstra’s Algorithm when heuristic is accurate.**  
✅ **Used in AI (pathfinding in games, robotics, maps, etc.).**  
❌ **Consumes more memory than Dijkstra’s due to storing heuristic values.**  
