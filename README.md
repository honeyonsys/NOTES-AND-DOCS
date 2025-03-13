

---

## **B U B B L E - S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Bubble Sort** algorithm.  

---

### **Real-World Example: Arranging Books by Height**  
Imagine you have a row of books on a shelf, but they are in random order based on height. You want to arrange them from **shortest to tallest** using the following approach:  
1. Compare the first two books. If the first book is **taller**, swap them.  
2. Move to the next pair and do the same.  
3. Repeat this process for the entire row until no swaps are needed.  

This is exactly how **Bubble Sort** works! The heaviest (largest) item "bubbles up" to the end with each pass.  

---

### **Solution Explanation**  
1. **Compare adjacent elements** in the array.  
2. **Swap them** if they are in the wrong order.  
3. **Repeat** the process for all elements, reducing the comparison range in each pass.  
4. Stop when no swaps are needed, meaning the array is sorted.  

### **Time Complexity**  
- **Best Case:** \(O(n)\) (if the array is already sorted)  
- **Average & Worst Case:** \(O(n^2)\) (when the array is in reverse order)  

---

### **Java Code Implementation (Optimized Bubble Sort)**  
```java
public class BubbleSort {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        boolean swapped;

        for (int i = 0; i < n - 1; i++) {
            swapped = false;

            // Last i elements are already sorted, so no need to check them
            for (int j = 0; j < n - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) { 
                    // Swap arr[j] and arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }

            // If no two elements were swapped, the array is already sorted
            if (!swapped) {
                break;
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        System.out.println("Original Array:");
        printArray(arr);

        bubbleSort(arr);

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

### **Why Use Bubble Sort?**
- **Simple to understand and implement.**  
- **Works well for small datasets.**  
- **Not efficient for large datasets due to \(O(n^2)\) complexity.**  

---
---
---
---


## **S E L E C T I O N - S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Selection Sort** algorithm.  

---

### **Real-World Example: Arranging Students by Height**  
Imagine a group of students standing in a line in random order. You want to arrange them from **shortest to tallest** using the following approach:  
1. Find the **shortest** student in the group.  
2. Swap them with the **first** student in the line.  
3. Find the next **shortest** student from the remaining group and swap them with the **second** student.  
4. Repeat the process until the entire line is sorted.  

This is exactly how **Selection Sort** works!  

---

### **Solution Explanation**  
1. **Find the smallest element** in the unsorted portion of the array.  
2. Swap it with the **first element** of the unsorted portion.  
3. Move to the next element and **repeat** the process until the array is sorted.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(n^2)\) (since it always goes through the full array to find the minimum)  
- **Advantage:** Unlike Bubble Sort, **Selection Sort** makes fewer swaps, making it more efficient in terms of memory writes.  

---

### **Java Code Implementation**  
```java
public class SelectionSort {
    public static void selectionSort(int[] arr) {
        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {
            int minIndex = i; // Assume the first element is the smallest
            
            // Find the minimum element in the remaining unsorted array
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }

            // Swap the found minimum element with the first element of the unsorted part
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        System.out.println("Original Array:");
        printArray(arr);

        selectionSort(arr);

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

### **Why Use Selection Sort?**
✅ **Fewer swaps than Bubble Sort** (better for memory-limited environments).  
✅ **Easy to implement and understand.**  
❌ **Not efficient for large datasets** (\(O(n^2)\) complexity).  

---
---
---
---


## **I N S E R T I O N  -  S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Insertion Sort** algorithm.  

---

### **Real-World Example: Sorting Playing Cards in Hand**  
Imagine you are playing a card game and receive cards **one by one**. You want to arrange them in order:  
1. Take the first card and place it in your hand.  
2. Take the next card and insert it into the correct position relative to the first.  
3. Repeat this process for each new card, shifting other cards if needed, until all are sorted.  

This is exactly how **Insertion Sort** works! It builds a sorted array **one element at a time** by inserting elements into their correct positions.  

---

### **Solution Explanation**  
1. Assume the **first element** is already sorted.  
2. Pick the **next element** and compare it with elements in the sorted portion.  
3. **Shift elements** in the sorted portion if they are greater than the current element.  
4. Insert the current element into its correct position.  
5. Repeat for all elements until the array is sorted.  

### **Time Complexity**  
- **Best Case:** \(O(n)\) (if the array is already sorted)  
- **Average & Worst Case:** \(O(n^2)\) (when the array is in reverse order)  

---

### **Java Code Implementation**  
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

### **Why Use Insertion Sort?**
✅ **Efficient for small or nearly sorted arrays** (\(O(n)\) in best case).  
✅ **In-place sorting** (does not require extra space).  
✅ **Stable sort** (preserves order of equal elements).  
❌ **Not efficient for large datasets** (\(O(n^2)\) complexity).  

---
---
---
---


## **M E R G E - S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Merge Sort** algorithm.  

---

### **Real-World Example: Merging Sorted Playlists**  
Imagine you have two separate playlists of songs, each sorted by popularity. You want to combine them into **one sorted playlist** without disturbing the order. You do this by:  
1. Taking the first song from each playlist.  
2. Comparing them and adding the **smaller one** to the final playlist.  
3. Repeating the process until both playlists are merged.  

This is exactly how **Merge Sort** works! It divides the array into smaller parts, sorts them, and then merges them back together.  

---

### **Solution Explanation**  
1. **Divide** the array into two halves until each sub-array has only one element.  
2. **Sort & Merge** the sub-arrays by comparing elements and combining them in sorted order.  
3. **Repeat** this process until the entire array is merged back into a sorted sequence.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(n \log n)\) (since the array is repeatedly divided and merged).  
- **Space Complexity:** \(O(n)\) (requires additional space for merging).  

---

### **Java Code Implementation (Recursive Approach)**  
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

### **Why Use Merge Sort?**
✅ **Efficient for large datasets** (\(O(n \log n)\) complexity).  
✅ **Stable sort** (preserves order of equal elements).  
✅ **Good for external sorting** (works well with disk storage).  
❌ **Requires extra space** (\(O(n)\) for temporary arrays).  

---
---
---
---

