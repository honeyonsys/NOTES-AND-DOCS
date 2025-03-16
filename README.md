

## **Fibonacci Sequence**  

---

### **Problem Statement**  
The **Fibonacci sequence** is a series of numbers where each number is the **sum of the two preceding ones**, starting from **0 and 1**.  

\[
F(n) = F(n-1) + F(n-2)
\]

With base cases:  
\[
F(0) = 0, \quad F(1) = 1
\]

The sequence starts as:  
**0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...**

---

### **Real-World Example: Rabbit Population Growth**  
Imagine a pair of rabbits:  
- They take **1 month** to mature.  
- After that, they produce **one new pair every month**.  
- The number of rabbit pairs **follows the Fibonacci sequence**!  

After **n months**, the number of rabbit pairs is given by **F(n)**.

---

## **Solution Explanation**  

### **1. Recursive Approach (Naïve)**
- Uses the **mathematical recurrence relation**.  
- **Time Complexity**: **\( O(2^n) \)** (exponential).  
- **Space Complexity**: **\( O(n) \)** (due to recursion depth).  

### **2. Dynamic Programming (Memoization)**
- Stores computed Fibonacci values to **avoid redundant calculations**.  
- **Time Complexity**: **\( O(n) \)**.  
- **Space Complexity**: **\( O(n) \)**.  

### **3. Iterative Approach**
- Uses a **loop instead of recursion**.  
- **Time Complexity**: **\( O(n) \)**.  
- **Space Complexity**: **\( O(1) \)** (only two variables stored).  

### **4. Matrix Exponentiation (Optimized)**
- Uses matrix multiplication to compute Fibonacci in **\( O(\log n) \)** time.  

---

## **Java Code Implementation**

### **1. Recursive Approach**
```java
class FibonacciRecursive {
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
    }
}
```

---

### **2. Dynamic Programming (Memoization)**
```java
import java.util.HashMap;

class FibonacciMemoization {
    static HashMap<Integer, Integer> memo = new HashMap<>();

    public static int fibonacci(int n) {
        if (n <= 1) return n;
        if (memo.containsKey(n)) return memo.get(n);
        
        int result = fibonacci(n - 1) + fibonacci(n - 2);
        memo.put(n, result);
        return result;
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
    }
}
```

---

### **3. Iterative Approach (Best for Large n)**
```java
class FibonacciIterative {
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        
        int a = 0, b = 1, c;
        for (int i = 2; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return b;
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
    }
}
```

---

### **4. Matrix Exponentiation (Optimized)**
```java
class FibonacciMatrix {
    public static int fibonacci(int n) {
        if (n == 0) return 0;
        int[][] F = {{1, 1}, {1, 0}};
        power(F, n - 1);
        return F[0][0];
    }

    public static void power(int[][] F, int n) {
        if (n == 0 || n == 1) return;
        int[][] M = {{1, 1}, {1, 0}};

        power(F, n / 2);
        multiply(F, F);

        if (n % 2 != 0) multiply(F, M);
    }

    public static void multiply(int[][] F, int[][] M) {
        int x = F[0][0] * M[0][0] + F[0][1] * M[1][0];
        int y = F[0][0] * M[0][1] + F[0][1] * M[1][1];
        int z = F[1][0] * M[0][0] + F[1][1] * M[1][0];
        int w = F[1][0] * M[0][1] + F[1][1] * M[1][1];

        F[0][0] = x;
        F[0][1] = y;
        F[1][0] = z;
        F[1][1] = w;
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
    }
}
```

---

## **Why Use Fibonacci Sequence?**  
✅ **Found in nature (sunflowers, pine cones, etc.).**  
✅ **Used in stock market analysis and financial modeling.**  
✅ **Optimized Fibonacci algorithms are used in competitive programming.**  
✅ **Used in Dynamic Programming examples and algorithmic problems.**  

---
---
---
---

# **Knapsack Problem**  

---

## **Problem Statement**  
Given a set of **items**, each with:  
- A **weight**  
- A **value**  

Determine the **maximum value** that can be obtained by selecting a subset of items such that the **total weight does not exceed a given capacity**.

---

### **Types of Knapsack Problems**
1. **0/1 Knapsack**  
   - Each item **can be included or not included** (no fractions).  
   - **Example**: Picking laptops for travel where each laptop is either taken or left.  

2. **Fractional Knapsack (Greedy Algorithm)**  
   - Items **can be broken into smaller parts**.  
   - **Example**: Filling a fuel tank with different types of fuel where partial amounts can be used.  

---

## **Real-World Example: Traveling with Limited Luggage Capacity**  
Imagine you are going on a **trip** and have a backpack with a **weight limit of 10 kg**. You have several **items (laptop, camera, books, snacks, etc.), each with a specific weight and value**.  

The goal is to **maximize the value of items packed while staying within the weight limit**.

---

## **Solution Explanation**  

### **1. 0/1 Knapsack (Dynamic Programming Approach)**
- Uses **bottom-up DP** to find the **optimal solution**.  
- **Time Complexity**: **\( O(nW) \)** where **n** is the number of items and **W** is the capacity.  
- **Space Complexity**: **\( O(nW) \)** (can be optimized to **\( O(W) \)**).  

---

### **2. Fractional Knapsack (Greedy Approach)**
- Sort items by **value/weight ratio**.  
- Pick **full items first**, then take a **fraction** of the last item.  
- **Time Complexity**: **\( O(n \log n) \)** (due to sorting).  
- **Space Complexity**: **\( O(1) \)**.  

---

## **Java Code Implementation**  

### **1. 0/1 Knapsack (Dynamic Programming)**
```java
class Knapsack01 {
    public static int knapsack(int W, int[] weights, int[] values, int n) {
        int[][] dp = new int[n + 1][W + 1];

        for (int i = 1; i <= n; i++) {
            for (int w = 1; w <= W; w++) {
                if (weights[i - 1] <= w) {
                    dp[i][w] = Math.max(values[i - 1] + dp[i - 1][w - weights[i - 1]], dp[i - 1][w]);
                } else {
                    dp[i][w] = dp[i - 1][w];
                }
            }
        }
        return dp[n][W];
    }

    public static void main(String[] args) {
        int W = 10;
        int[] weights = {2, 3, 4, 5};
        int[] values = {3, 4, 5, 6};
        int n = weights.length;

        System.out.println("Maximum value: " + knapsack(W, weights, values, n));
    }
}
```

---

### **2. Fractional Knapsack (Greedy Algorithm)**
```java
import java.util.Arrays;

class Item {
    int weight, value;
    
    Item(int value, int weight) {
        this.value = value;
        this.weight = weight;
    }
}

class KnapsackFractional {
    public static double fractionalKnapsack(int W, Item[] items) {
        Arrays.sort(items, (a, b) -> Double.compare((double) b.value / b.weight, (double) a.value / a.weight));

        double totalValue = 0;
        for (Item item : items) {
            if (W >= item.weight) {
                W -= item.weight;
                totalValue += item.value;
            } else {
                totalValue += ((double) item.value / item.weight) * W;
                break;
            }
        }
        return totalValue;
    }

    public static void main(String[] args) {
        Item[] items = {new Item(60, 10), new Item(100, 20), new Item(120, 30)};
        int W = 50;

        System.out.println("Maximum value: " + fractionalKnapsack(W, items));
    }
}
```

---

## **Why Use Knapsack Algorithm?**  
✅ **Used in financial portfolio optimization (maximizing profit within a budget).**  
✅ **Used in resource allocation problems (scheduling, caching, cloud computing).**  
✅ **Used in e-commerce (recommendation systems based on customer constraints).**  


