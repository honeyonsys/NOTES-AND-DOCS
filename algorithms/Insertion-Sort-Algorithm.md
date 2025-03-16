# **I N S E R T I O N  -  S O R T**  
## **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Insertion Sort** algorithm.  

---

## **Real-World Example: Sorting Playing Cards in Hand**  
Imagine you are playing a card game and receive cards **one by one**. You want to arrange them in order:  
1. Take the first card and place it in your hand.  
2. Take the next card and insert it into the correct position relative to the first.  
3. Repeat this process for each new card, shifting other cards if needed, until all are sorted.  

This is exactly how **Insertion Sort** works! It builds a sorted array **one element at a time** by inserting elements into their correct positions.  

---

## **Solution Explanation**  
1. Assume the **first element** is already sorted.  
2. Pick the **next element** and compare it with elements in the sorted portion.  
3. **Shift elements** in the sorted portion if they are greater than the current element.  
4. Insert the current element into its correct position.  
5. Repeat for all elements until the array is sorted.  

## **Time Complexity**  
- **Best Case:** \(O(n)\) (if the array is already sorted)  
- **Average & Worst Case:** \(O(n^2)\) (when the array is in reverse order)  

---

## **Java Code Implementation**  
```java
public class InsertionSort {
    public static void insertionSort(int[] arr) {
        int n = arr.length;
        
        for (int i = 1; i < n; i++) {
            int key = arr[i]; // Current element to be inserted
            int j = i - 1;

            // Move elements that are greater than key one position ahead
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }
            
            // Insert the key at its correct position
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6};
        System.out.println("Original Array:");
        printArray(arr);

        insertionSort(arr);

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

## **Why Use Insertion Sort?**
✅ **Efficient for small or nearly sorted arrays** (\(O(n)\) in best case).  
✅ **In-place sorting** (does not require extra space).  
✅ **Stable sort** (preserves order of equal elements).  
❌ **Not efficient for large datasets** (\(O(n^2)\) complexity).  
