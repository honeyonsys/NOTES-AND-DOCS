# **T O P O L O G I C A L - S O R T I N G**  

---

## **Problem Statement**  
Given a **Directed Acyclic Graph (DAG)**, find a **linear ordering of its vertices** such that for every directed edge **(u → v)**, vertex **u** comes **before** vertex **v** in the ordering.  

- **Topological Sorting** is **only possible for DAGs (graphs without cycles)**.  
- It is widely used in **dependency resolution problems** (e.g., task scheduling).  

---

## **Real-World Example: Course Prerequisites**  
Imagine a university course structure where:  
- **Each course is a node**.  
- **A directed edge (A → B) means course A is a prerequisite for course B**.  
- We must **find an order** to take courses so that all prerequisites are satisfied.  
- **Topological Sorting** provides the correct sequence.

---

## **Solution Explanation**  
There are two main approaches:  

## **1. Kahn’s Algorithm (BFS-Based Approach)**
1. Compute **in-degree** (number of incoming edges) for each node.  
2. Add all **nodes with in-degree 0** to a queue.  
3. While the queue is not empty:  
   - Remove a node from the queue and add it to the result.  
   - Reduce the in-degree of its neighbors.  
   - If any neighbor’s in-degree becomes **0**, add it to the queue.  
4. If all nodes are processed, the result is a valid **topological order**.  

**Time Complexity**: \(O(V + E)\) (traverses all vertices and edges once).  

## **2. DFS-Based Approach**  
1. Perform **DFS traversal** and store the nodes in a **stack** after processing all its neighbors.  
2. The final stack contains nodes in **topological order** (reverse of finish time).  

**Time Complexity**: \(O(V + E)\) (DFS traversal).  

---

# **Java Code Implementation**

## **1. Kahn’s Algorithm (BFS Approach)**
```java
import java.util.*;

class TopologicalSortKahn {
    public static void topologicalSort(int V, List<List<Integer>> adj) {
        int[] inDegree = new int[V];
        for (List<Integer> neighbors : adj) {
            for (int neighbor : neighbors) {
                inDegree[neighbor]++;
            }
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < V; i++) {
            if (inDegree[i] == 0) queue.add(i);
        }

        List<Integer> topoOrder = new ArrayList<>();
        while (!queue.isEmpty()) {
            int node = queue.poll();
            topoOrder.add(node);
            for (int neighbor : adj.get(node)) {
                if (--inDegree[neighbor] == 0) {
                    queue.add(neighbor);
                }
            }
        }

        if (topoOrder.size() != V) {
            System.out.println("Graph contains a cycle! Topological sorting not possible.");
        } else {
            System.out.println("Topological Order: " + topoOrder);
        }
    }

    public static void main(String[] args) {
        int V = 6;
        List<List<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < V; i++) adj.add(new ArrayList<>());

        adj.get(5).add(2);
        adj.get(5).add(0);
        adj.get(4).add(0);
        adj.get(4).add(1);
        adj.get(2).add(3);
        adj.get(3).add(1);

        topologicalSort(V, adj);
    }
}
```

---

## **2. DFS-Based Approach**
```java
import java.util.*;

class TopologicalSortDFS {
    public static void dfs(int node, List<List<Integer>> adj, boolean[] visited, Stack<Integer> stack) {
        visited[node] = true;
        for (int neighbor : adj.get(node)) {
            if (!visited[neighbor]) {
                dfs(neighbor, adj, visited, stack);
            }
        }
        stack.push(node);
    }

    public static void topologicalSort(int V, List<List<Integer>> adj) {
        Stack<Integer> stack = new Stack<>();
        boolean[] visited = new boolean[V];

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                dfs(i, adj, visited, stack);
            }
        }

        System.out.print("Topological Order: ");
        while (!stack.isEmpty()) {
            System.out.print(stack.pop() + " ");
        }
    }

    public static void main(String[] args) {
        int V = 6;
        List<List<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < V; i++) adj.add(new ArrayList<>());

        adj.get(5).add(2);
        adj.get(5).add(0);
        adj.get(4).add(0);
        adj.get(4).add(1);
        adj.get(2).add(3);
        adj.get(3).add(1);

        topologicalSort(V, adj);
    }
}
```

---

## **Why Use Topological Sorting?**  
✅ **Used in scheduling tasks (e.g., dependency resolution in project management, software builds, etc.).**  
✅ **Helps detect cycles in DAGs.**  
✅ **Used in compiler optimization (instruction reordering).**  
❌ **Only works for Directed Acyclic Graphs (DAGs), not general graphs.**  
