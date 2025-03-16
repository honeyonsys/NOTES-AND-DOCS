# **Q U I C K - S O R T**  
## **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Quick Sort** algorithm.  

---

## **Real-World Example: Arranging Books Around a Pivot**  
Imagine you have a messy bookshelf and want to organize it by **height** using the following approach:  
1. Pick a random book as the **pivot**.  
2. Move all books **shorter** than the pivot to the **left** and all books **taller** than the pivot to the **right**.  
3. Repeat this process for the left and right sections until the entire bookshelf is sorted.  

This is exactly how **Quick Sort** works! It divides and conquers the problem by repeatedly **partitioning** the array around a pivot element.  

---

## **Solution Explanation**  
1. **Choose a Pivot:** Pick an element (usually the last element, first element, or a random element).  
2. **Partitioning:** Rearrange the array so that:  
   - Elements **smaller** than the pivot move to the **left**.  
   - Elements **greater** than the pivot move to the **right**.  
3. **Recursively Apply Quick Sort:** Apply the same steps to the left and right partitions.  
4. The array gets sorted once all partitions are fully processed.  

## **Time Complexity**  
- **Best & Average Case:** \(O(n \log n)\) (efficient for large datasets).  
- **Worst Case:** \(O(n^2)\) (if the pivot selection is poor, e.g., always choosing the smallest/largest element in an already sorted array).  

---

## **Java Code Implementation (Lomuto Partition Scheme)**  
```java
public class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            // Partition the array and get the pivot index
            int pivotIndex = partition(arr, low, high);

            // Recursively sort elements before and after partition
            quickSort(arr, low, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, high);
        }
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[high]; // Choosing last element as pivot
        int i = low - 1; // Index of smaller element

        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) {
                i++;
                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // Swap pivot element with the element at i+1 to place it in correct position
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        return i + 1;
    }

    public static void main(String[] args) {
        int[] arr = {10, 80, 30, 90, 40, 50, 70};
        System.out.println("Original Array:");
        printArray(arr);

        quickSort(arr, 0, arr.length - 1);

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

## **Why Use Quick Sort?**
✅ **Faster than Merge Sort** in practice (less memory overhead).  
✅ **In-place sorting** (does not require extra space like Merge Sort).  
✅ **Works well for large datasets** (especially when pivot is chosen wisely).  
❌ **Worst case is \(O(n^2)\)** (if pivot selection is poor).  
❌ **Not a stable sort** (may not preserve the order of equal elements).  
