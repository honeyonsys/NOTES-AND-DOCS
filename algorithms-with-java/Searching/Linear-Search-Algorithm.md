# **L I N E A R - S E A R C H**  
## **Problem Statement**  
Given an **unsorted array** and a **target value**, find the index of the target value using the **Linear Search** algorithm. If the value is not found, return **-1**.  

---

## **Real-World Example: Finding a Book in a Stack**  
Imagine you have a **stack of books** in no particular order, and you need to find a specific book. The best way is to:  
1. Start from the **first book** and check if it’s the one you need.  
2. If not, move to the **next book** and check again.  
3. Repeat this process until you find the book or reach the end of the stack.  

This is exactly how **Linear Search** works—it sequentially checks each element until it finds the target.  

---

## **Solution Explanation**  
1. **Start from the first element** of the array.  
2. **Compare each element** with the target value.  
3. If a **match is found**, return the **index**.  
4. If the loop finishes and no match is found, return **-1**.  

## **Time Complexity**  
- **Best Case:** \(O(1)\) (if the target is the first element).  
- **Worst & Average Case:** \(O(n)\) (if the target is at the end or not present).  

## **Space Complexity:** \(O(1)\) (no extra memory is used).  

---

## **Java Code Implementation (Iterative Approach)**  
```java
public class LinearSearch {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i; // Return index if found
            }
        }
        return -1; // Return -1 if not found
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        int target = 30;

        int result = linearSearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

## **Java Code Implementation (Recursive Approach)**  
```java
public class LinearSearchRecursive {
    public static int linearSearch(int[] arr, int target, int index) {
        if (index >= arr.length) {
            return -1; // Base case: not found
        }
        if (arr[index] == target) {
            return index; // Element found
        }
        return linearSearch(arr, target, index + 1); // Recursive call
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        int target = 40;

        int result = linearSearch(arr, target, 0);
        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

## **Why Use Linear Search?**
✅ **Simple and easy to implement**  
✅ **Works for both sorted & unsorted arrays**  
✅ **Useful for small datasets**  
❌ **Slow for large datasets** (\(O(n)\) complexity)  
❌ **Inefficient compared to Binary Search for sorted arrays**  
