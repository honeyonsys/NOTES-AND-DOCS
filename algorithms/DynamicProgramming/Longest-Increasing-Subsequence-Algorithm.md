# **Longest Increasing Subsequence (LIS)**  

---

## **Problem Statement**  
Given an array of integers, **find the length of the longest subsequence** such that **all elements are in increasing order**.  
A **subsequence** is a sequence derived from another sequence by **removing some elements (possibly none) without changing the order of the remaining elements**.  

### **Example**  
**Input:** `arr = [10, 22, 9, 33, 21, 50, 41, 60, 80]`  
**Output:** `LIS length = 6`  
**LIS = [10, 22, 33, 50, 60, 80]`  

---

## **Real-World Example: Stock Market Prediction**  
In financial analysis, the **LIS algorithm** can be used to analyze stock price trends.  
For example, if stock prices are `[100, 110, 90, 115, 120, 95, 130]`,  
the longest increasing sequence (`LIS`) is `[100, 110, 115, 120, 130]`.  

This helps investors identify **long-term growth trends**.

---

## **Solution Explanation**  

### **1. Recursive Approach (Brute Force)**
- Check all **subsequences** recursively.
- If the next element is greater, include it and check further.
- **Time Complexity**: **\( O(2^n) \)** (exponential).  

### **2. Dynamic Programming (Optimized)**
- Use a **dp array**, where `dp[i]` stores the LIS ending at index `i`.
- **Formula:**  
  \[
  dp[i] = \max(dp[j] + 1) \quad \text{for all } j < i \text{ where } arr[j] < arr[i]
  \]
- **Time Complexity**: **\( O(n^2) \)**.  
- **Space Complexity**: **\( O(n) \)**.  

### **3. Binary Search + Dynamic Programming (Most Efficient)**
- Use **Binary Search** and **Greedy** approach with a **temporary array (`temp`)**.  
- Instead of maintaining LIS, store potential subsequence elements.  
- **Time Complexity**: **\( O(n \log n) \)** (using `Binary Search`).  
- **Space Complexity**: **\( O(n) \)**.  

---

## **Java Code Implementation**  

### **1. Dynamic Programming Approach (O(n²))**
```java
class LISDP {
    public static int lis(int[] arr) {
        int n = arr.length;
        int[] dp = new int[n];
        int maxLIS = 1;

        for (int i = 0; i < n; i++) {
            dp[i] = 1; // Every element is an LIS of length 1
            for (int j = 0; j < i; j++) {
                if (arr[j] < arr[i]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLIS = Math.max(maxLIS, dp[i]);
        }
        return maxLIS;
    }

    public static void main(String[] args) {
        int[] arr = {10, 22, 9, 33, 21, 50, 41, 60, 80};
        System.out.println("Length of LIS: " + lis(arr));
    }
}
```

---

### **2. Optimized Approach (Binary Search + DP) \( O(n \log n) \)**
```java
import java.util.*;

class LISBinarySearch {
    public static int lis(int[] arr) {
        ArrayList<Integer> temp = new ArrayList<>();
        for (int num : arr) {
            int index = Collections.binarySearch(temp, num);
            if (index < 0) index = -(index + 1);
            if (index == temp.size()) temp.add(num);
            else temp.set(index, num);
        }
        return temp.size();
    }

    public static void main(String[] args) {
        int[] arr = {10, 22, 9, 33, 21, 50, 41, 60, 80};
        System.out.println("Length of LIS: " + lis(arr));
    }
}
```

---

## **Why Use LIS Algorithm?**  
✅ **Used in stock market analysis (predicting price trends).**  
✅ **Used in longest chain formation in networking problems.**  
✅ **Used in gaming (ranking and level progression analysis).**  
