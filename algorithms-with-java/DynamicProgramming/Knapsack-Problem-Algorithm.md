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
