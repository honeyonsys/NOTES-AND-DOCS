# **H E A P - S O R T**  
## **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Heap Sort** algorithm.  

---

## **Real-World Example: Priority Queue in a To-Do List**  
Imagine you have a **to-do list** with tasks of varying importance. To efficiently complete them, you arrange them in a **priority queue**, always handling the **most important task first**.  
1. Convert the list into a **heap structure** (max-heap where the highest priority is on top).  
2. Remove the **highest priority task** (root of the heap) and move the last task to the root.  
3. **Rearrange** the heap to maintain order.  
4. Repeat until all tasks are completed in priority order.  

This is exactly how **Heap Sort** works! It builds a heap and repeatedly extracts the largest element to sort the array.  

---

## **Solution Explanation**  
1. **Build a Max-Heap**: Convert the array into a **binary heap** where the largest element is at the root.  
2. **Extract Elements**: Remove the root (largest element), place it at the end of the array, and **heapify** the remaining elements.  
3. **Repeat Until Sorted**: Continue extracting the maximum element and heapifying until the array is fully sorted.  

## **Heap Properties**  
- **Max-Heap**: Parent node is always **greater than** its child nodes.  
- **Min-Heap**: Parent node is always **smaller than** its child nodes.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(n \log n)\) (efficient for large datasets).  
- **Space Complexity:** \(O(1)\) (in-place sorting, no extra memory used).  

---

## **Java Code Implementation**  
```java
public class HeapSort {
    public static void heapSort(int[] arr) {
        int n = arr.length;

        // Step 1: Build a max heap
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }

        // Step 2: Extract elements one by one
        for (int i = n - 1; i > 0; i--) {
            // Move current root (largest) to the end
            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;

            // Heapify the reduced heap
            heapify(arr, i, 0);
        }
    }

    private static void heapify(int[] arr, int n, int i) {
        int largest = i; // Root node
        int left = 2 * i + 1; // Left child
        int right = 2 * i + 2; // Right child

        // If left child is larger than root
        if (left < n && arr[left] > arr[largest]) {
            largest = left;
        }

        // If right child is larger than largest so far
        if (right < n && arr[right] > arr[largest]) {
            largest = right;
        }

        // If largest is not root, swap and heapify again
        if (largest != i) {
            int swap = arr[i];
            arr[i] = arr[largest];
            arr[largest] = swap;

            // Recursively heapify the affected sub-tree
            heapify(arr, n, largest);
        }
    }

    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6, 7};
        System.out.println("Original Array:");
        printArray(arr);

        heapSort(arr);

        System.out.println("Sorted Array:");
        printArray(arr);
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

---

## **Why Use Heap Sort?**
✅ **Always \(O(n \log n)\) complexity** (better worst-case performance than Quick Sort).  
✅ **In-place sorting** (does not require extra memory).  
✅ **Efficient for large datasets** (often used in priority queues & scheduling).  
❌ **Not a stable sort** (may not preserve order of equal elements).  
❌ **Heapifying adds overhead** (slower than Quick Sort in practice).  

