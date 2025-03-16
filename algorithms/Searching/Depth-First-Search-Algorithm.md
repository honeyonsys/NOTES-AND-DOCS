# **D E P T H - F I R S T - S E A R C H - (DFS)**  
## **Problem Statement**  
Given a **graph or tree**, traverse all the nodes using the **Depth First Search (DFS)** algorithm.  

DFS explores as **deep as possible** in one direction before backtracking. It can be implemented using **recursion (implicit stack)** or **iteration (explicit stack)**.  

---

## **Real-World Example: Solving a Maze**  
Imagine you are inside a **maze**, and your goal is to find the **exit**.  

1. You start at the **entrance** and choose a **random path**.  
2. You continue moving **deeper** into the maze.  
3. If you reach a **dead-end**, you backtrack to the **previous decision point** and try another path.  
4. You repeat this process until you find the **exit**.  

DFS works in a similar way—it explores a path **deeply** before backtracking.  

---

## **Solution Explanation**  
DFS is useful for problems where you need to explore all possible paths before deciding. It can be applied to both **graphs** and **trees**.  

### **DFS Algorithm (Recursive Approach)**  
1. **Start from a node** and mark it as **visited**.  
2. **Visit all adjacent unvisited nodes**, one by one.  
3. **For each adjacent node, recursively perform DFS**.  
4. **Backtrack** when no more unvisited adjacent nodes are left.  

### **DFS Algorithm (Iterative Approach - Using Stack)**  
1. **Push the starting node** onto a **stack**.  
2. **While the stack is not empty**:
   - Pop a node from the stack.  
   - If it’s unvisited, **mark it as visited** and push its **unvisited adjacent nodes** onto the stack.  
3. Repeat until all nodes are visited.  

## **Time Complexity**  
- **Worst, Best & Average Case:** \(O(V + E)\) (where \(V\) is the number of vertices and \(E\) is the number of edges).  

## **Space Complexity**  
- **Recursive DFS:** \(O(V)\) (due to recursive calls).  
- **Iterative DFS:** \(O(V)\) (due to stack usage).  

---

# **Java Code Implementation**  
## **DFS for Graph (Recursive Approach)**  
```java
import java.util.*;

public class DFSRecursive {
    static void dfs(Map<Integer, List<Integer>> graph, int node, Set<Integer> visited) {
        System.out.print(node + " ");
        visited.add(node);

        for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
            if (!visited.contains(neighbor)) {
                dfs(graph, neighbor, visited);
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

        System.out.println("DFS Traversal (Recursive):");
        dfs(graph, 0, new HashSet<>());  // Start DFS from node 0
    }
}
```

---

## **DFS for Graph (Iterative Approach - Using Stack)**  
```java
import java.util.*;

public class DFSIterative {
    static void dfs(Map<Integer, List<Integer>> graph, int start) {
        Stack<Integer> stack = new Stack<>();
        Set<Integer> visited = new HashSet<>();
        
        stack.push(start);

        while (!stack.isEmpty()) {
            int node = stack.pop();
            if (!visited.contains(node)) {
                System.out.print(node + " ");
                visited.add(node);

                // Push all adjacent nodes to stack (reverse order for correct order)
                List<Integer> neighbors = graph.getOrDefault(node, new ArrayList<>());
                Collections.reverse(neighbors);
                for (int neighbor : neighbors) {
                    if (!visited.contains(neighbor)) {
                        stack.push(neighbor);
                    }
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

        System.out.println("DFS Traversal (Iterative):");
        dfs(graph, 0);  // Start DFS from node 0
    }
}
```

---

### **Why Use DFS?**
✅ **Efficient for exploring deep paths in graphs or trees**.  
✅ **Uses less memory compared to Breadth First Search (BFS)** for dense graphs.  
✅ **Can be used to detect cycles in graphs**.  
✅ **Useful for topological sorting, solving mazes, and connectivity checks**.  
❌ **Not always the shortest path (unlike BFS)**.  
