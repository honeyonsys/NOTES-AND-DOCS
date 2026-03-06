# **M E R G E - S O R T**  
## **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Merge Sort** algorithm.  

---

## **Real-World Example: Merging Sorted Playlists**  
Imagine you have two separate playlists of songs, each sorted by popularity. You want to combine them into **one sorted playlist** without disturbing the order. You do this by:  
1. Taking the first song from each playlist.  
2. Comparing them and adding the **smaller one** to the final playlist.  
3. Repeating the process until both playlists are merged.  

This is exactly how **Merge Sort** works! It divides the array into smaller parts, sorts them, and then merges them back together.  

---

## **Solution Explanation**  
1. **Divide** the array into two halves until each sub-array has only one element.  
2. **Sort & Merge** the sub-arrays by comparing elements and combining them in sorted order.  
3. **Repeat** this process until the entire array is merged back into a sorted sequence.  

## **Time Complexity**  
- **Best, Average & Worst Case:** \(O(n \log n)\) (since the array is repeatedly divided and merged).  
- **Space Complexity:** \(O(n)\) (requires additional space for merging).  

---

## **Java Code Implementation (Recursive Approach)**  
```java
public class MergeSort {
    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = left + (right - left) / 2;

            // Recursively sort first and second halves
            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);

            // Merge the sorted halves
            merge(arr, left, mid, right);
        }
    }

    private static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // Create temporary arrays
        int[] leftArr = new int[n1];
        int[] rightArr = new int[n2];

        // Copy data to temporary arrays
        for (int i = 0; i < n1; i++)
            leftArr[i] = arr[left + i];
        for (int j = 0; j < n2; j++)
            rightArr[j] = arr[mid + 1 + j];

        int i = 0, j = 0, k = left;

        // Merge the two subarrays
        while (i < n1 && j < n2) {
            if (leftArr[i] <= rightArr[j]) {
                arr[k] = leftArr[i];
                i++;
            } else {
                arr[k] = rightArr[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements of leftArr[] if any
        while (i < n1) {
            arr[k] = leftArr[i];
            i++;
            k++;
        }

        // Copy remaining elements of rightArr[] if any
        while (j < n2) {
            arr[k] = rightArr[j];
            j++;
            k++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {38, 27, 43, 3, 9, 82, 10};
        System.out.println("Original Array:");
        printArray(arr);

        mergeSort(arr, 0, arr.length - 1);

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

## **Why Use Merge Sort?**
✅ **Efficient for large datasets** (\(O(n \log n)\) complexity).  
✅ **Stable sort** (preserves order of equal elements).  
✅ **Good for external sorting** (works well with disk storage).  
❌ **Requires extra space** (\(O(n)\) for temporary arrays).  
