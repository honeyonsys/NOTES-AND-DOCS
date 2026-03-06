# **B I N A R Y - S E A R C H**  
## **Problem Statement**  
Given a **sorted array** and a **target value**, find the index of the target using the **Binary Search** algorithm. If the value is not found, return **-1**.  

---

## **Real-World Example: Looking Up a Word in a Dictionary**  
Imagine you are searching for a word in a **dictionary**. Instead of checking page by page like **Linear Search**, you:  
1. Open the dictionary **in the middle** and check if the word is there.  
2. If the word comes **before the middle**, search in the **left half**.  
3. If the word comes **after the middle**, search in the **right half**.  
4. Repeat until you find the word or determine it's missing.  

This **divide and conquer** approach makes **Binary Search** much faster than **Linear Search**.  

---

## **Solution Explanation**  
1. **Find the middle element** of the array.  
2. Compare the middle element with the **target value**:
   - If **equal**, return the **index**.  
   - If **smaller**, search the **right half** of the array.  
   - If **larger**, search the **left half** of the array.  
3. Repeat until the target is found or the search range is empty.  

## **Time Complexity**  
- **Best Case:** \(O(1)\) (if the middle element is the target).  
- **Worst & Average Case:** \(O(\log n)\) (efficient for large datasets).  

## **Space Complexity**  
- **Iterative Approach:** \(O(1)\) (no extra memory used).  
- **Recursive Approach:** \(O(\log n)\) (due to recursive calls).  

---

## **Java Code Implementation**  
### **Iterative Approach**  
```java
public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid; // Target found
            } else if (arr[mid] < target) {
                left = mid + 1; // Search right half
            } else {
                right = mid - 1; // Search left half
            }
        }
        return -1; // Target not found
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50, 60, 70};
        int target = 40;

        int result = binarySearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

### **Recursive Approach**  
```java
public class BinarySearchRecursive {
    public static int binarySearch(int[] arr, int left, int right, int target) {
        if (left > right) {
            return -1; // Base case: target not found
        }

        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid; // Target found
        } else if (arr[mid] < target) {
            return binarySearch(arr, mid + 1, right, target); // Search right half
        } else {
            return binarySearch(arr, left, mid - 1, target); // Search left half
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50, 60, 70};
        int target = 50;

        int result = binarySearch(arr, 0, arr.length - 1, target);
        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

### **Why Use Binary Search?**
✅ **Much faster than Linear Search** (\(O(\log n)\) vs. \(O(n)\)).  
✅ **Efficient for large datasets**.  
✅ **Works well with sorted data (arrays, databases, etc.)**.  
❌ **Only works on sorted arrays**.  
❌ **More complex than Linear Search**.  
