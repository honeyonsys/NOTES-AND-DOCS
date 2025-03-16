# **J U M P - S E A R C H**  

---

## **Problem Statement**  
Given a **sorted array**, efficiently search for an element using the **Jump Search** algorithm.  

Jump Search is an **optimized searching algorithm** that is faster than **Linear Search (O(n))** but slightly slower than **Binary Search (O(log n))**. It works by **jumping ahead** in fixed steps instead of checking elements one by one.  

---

## **Real-World Example: Searching a Name in a Phone Book**  
Imagine you have a **phone book** containing names in **alphabetical order**. Instead of searching page by page (**Linear Search**) or always going to the middle (**Binary Search**), you **jump** a few pages ahead at a time to quickly reach the section containing the desired name.  

Once you reach a page where the name might be located, you then perform a **linear search** within that section.  

---

## **Solution Explanation**  
1. **Choose a step size** of \( \sqrt{n} \) (square root of array size).  
2. **Jump ahead** in steps of \( \sqrt{n} \) until you find a block where the target value might exist.  
3. Perform a **linear search** within this block.  
4. If found, return the index; otherwise, return -1.  

---

## **Time Complexity**  
- **Best Case:** \( O(1) \) (element found in the first jump).  
- **Worst Case:** \( O(\sqrt{n}) \) (element found in the last block).  
- **Average Case:** \( O(\sqrt{n}) \).  

## **Space Complexity**  
- \( O(1) \) (constant extra space).  

---

# **Java Code Implementation**
```java
public class JumpSearch {
    public static int jumpSearch(int[] arr, int target) {
        int n = arr.length;
        int step = (int) Math.sqrt(n);  // Optimal jump size
        int prev = 0;

        // Jumping in steps of sqrt(n)
        while (arr[Math.min(step, n) - 1] < target) {
            prev = step;
            step += (int) Math.sqrt(n);
            if (prev >= n) {
                return -1; // Element not found
            }
        }

        // Linear search within the identified block
        while (arr[prev] < target) {
            prev++;
            if (prev == Math.min(step, n)) {
                return -1; // Element not found
            }
        }

        // If element is found
        if (arr[prev] == target) {
            return prev;
        }

        return -1; // Element not found
    }

    public static void main(String[] args) {
        int[] arr = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
        int target = 23;

        int index = jumpSearch(arr, target);
        if (index != -1) {
            System.out.println("Element found at index: " + index);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

## **Why Use Jump Search?**
✅ **Faster than Linear Search for large datasets**.  
✅ **Efficient for sorted arrays**.  
✅ **Less memory usage compared to Binary Search (no recursion)**.  
❌ **Slower than Binary Search for larger arrays**.  
