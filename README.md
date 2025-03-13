

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

## **Q U I C K - S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Quick Sort** algorithm.  

---

### **Real-World Example: Arranging Books Around a Pivot**  
Imagine you have a messy bookshelf and want to organize it by **height** using the following approach:  
1. Pick a random book as the **pivot**.  
2. Move all books **shorter** than the pivot to the **left** and all books **taller** than the pivot to the **right**.  
3. Repeat this process for the left and right sections until the entire bookshelf is sorted.  

This is exactly how **Quick Sort** works! It divides and conquers the problem by repeatedly **partitioning** the array around a pivot element.  

---

### **Solution Explanation**  
1. **Choose a Pivot:** Pick an element (usually the last element, first element, or a random element).  
2. **Partitioning:** Rearrange the array so that:  
   - Elements **smaller** than the pivot move to the **left**.  
   - Elements **greater** than the pivot move to the **right**.  
3. **Recursively Apply Quick Sort:** Apply the same steps to the left and right partitions.  
4. The array gets sorted once all partitions are fully processed.  

### **Time Complexity**  
- **Best & Average Case:** \(O(n \log n)\) (efficient for large datasets).  
- **Worst Case:** \(O(n^2)\) (if the pivot selection is poor, e.g., always choosing the smallest/largest element in an already sorted array).  

---

### **Java Code Implementation (Lomuto Partition Scheme)**  
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

### **Why Use Quick Sort?**
✅ **Faster than Merge Sort** in practice (less memory overhead).  
✅ **In-place sorting** (does not require extra space like Merge Sort).  
✅ **Works well for large datasets** (especially when pivot is chosen wisely).  
❌ **Worst case is \(O(n^2)\)** (if pivot selection is poor).  
❌ **Not a stable sort** (may not preserve the order of equal elements).  

---
---
---
---


## **H E A P - S O R T**  
### **Problem Statement**  
Given an unsorted array, sort it in **ascending order** using the **Heap Sort** algorithm.  

---

### **Real-World Example: Priority Queue in a To-Do List**  
Imagine you have a **to-do list** with tasks of varying importance. To efficiently complete them, you arrange them in a **priority queue**, always handling the **most important task first**.  
1. Convert the list into a **heap structure** (max-heap where the highest priority is on top).  
2. Remove the **highest priority task** (root of the heap) and move the last task to the root.  
3. **Rearrange** the heap to maintain order.  
4. Repeat until all tasks are completed in priority order.  

This is exactly how **Heap Sort** works! It builds a heap and repeatedly extracts the largest element to sort the array.  

---

### **Solution Explanation**  
1. **Build a Max-Heap**: Convert the array into a **binary heap** where the largest element is at the root.  
2. **Extract Elements**: Remove the root (largest element), place it at the end of the array, and **heapify** the remaining elements.  
3. **Repeat Until Sorted**: Continue extracting the maximum element and heapifying until the array is fully sorted.  

### **Heap Properties**  
- **Max-Heap**: Parent node is always **greater than** its child nodes.  
- **Min-Heap**: Parent node is always **smaller than** its child nodes.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(n \log n)\) (efficient for large datasets).  
- **Space Complexity:** \(O(1)\) (in-place sorting, no extra memory used).  

---

### **Java Code Implementation**  
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

### **Why Use Heap Sort?**
✅ **Always \(O(n \log n)\) complexity** (better worst-case performance than Quick Sort).  
✅ **In-place sorting** (does not require extra memory).  
✅ **Efficient for large datasets** (often used in priority queues & scheduling).  
❌ **Not a stable sort** (may not preserve order of equal elements).  
❌ **Heapifying adds overhead** (slower than Quick Sort in practice).  

---
---
---
---


## **R A D I X - S O R T**  
### **Problem Statement**  
Given an array of **non-negative integers**, sort it in **ascending order** using the **Radix Sort** algorithm.  

---

### **Real-World Example: Sorting Mail by ZIP Code**  
Imagine you work at a **postal service** and need to **sort mail** based on ZIP codes. You can’t compare all ZIP codes at once, so you:  
1. Sort letters based on the **last digit** of the ZIP code.  
2. Sort again based on the **second last digit**.  
3. Continue this process until the ZIP codes are completely sorted.  

This is exactly how **Radix Sort** works! It sorts numbers **digit by digit**, starting from the least significant digit (LSD).  

---

### **Solution Explanation**  
Radix Sort works by sorting numbers based on individual digits, starting from the **least significant digit (LSD)** to the **most significant digit (MSD)**.  

#### **Steps to Perform Radix Sort:**  
1. **Find the maximum number** in the array to determine the number of digits.  
2. **Sort numbers digit by digit** using a **stable sorting algorithm** (usually **Counting Sort**).  
3. **Repeat for each digit**, moving from the **least significant digit (LSD)** to the **most significant digit (MSD)**.  
4. Once all digits are processed, the array becomes sorted.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(nk)\) (where \(n\) is the number of elements and \(k\) is the maximum number of digits).  
- **Space Complexity:** \(O(n + k)\) (due to extra space in Counting Sort).  

---

### **Java Code Implementation**  
```java
import java.util.Arrays;

public class RadixSort {
    public static void radixSort(int[] arr) {
        int max = getMax(arr);

        // Apply counting sort to each digit place (1s, 10s, 100s, etc.)
        for (int place = 1; max / place > 0; place *= 10) {
            countingSort(arr, place);
        }
    }

    private static int getMax(int[] arr) {
        int max = arr[0];
        for (int num : arr) {
            if (num > max) {
                max = num;
            }
        }
        return max;
    }

    private static void countingSort(int[] arr, int place) {
        int n = arr.length;
        int[] output = new int[n]; // Output array
        int[] count = new int[10]; // Counting array (digits 0-9)

        // Count occurrences of each digit at the current place value
        for (int num : arr) {
            int digit = (num / place) % 10;
            count[digit]++;
        }

        // Convert count array to cumulative count
        for (int i = 1; i < 10; i++) {
            count[i] += count[i - 1];
        }

        // Place numbers in sorted order based on the current digit
        for (int i = n - 1; i >= 0; i--) {
            int digit = (arr[i] / place) % 10;
            output[count[digit] - 1] = arr[i];
            count[digit]--;
        }

        // Copy the sorted values back into the original array
        System.arraycopy(output, 0, arr, 0, n);
    }

    public static void main(String[] args) {
        int[] arr = {170, 45, 75, 90, 802, 24, 2, 66};
        System.out.println("Original Array:");
        System.out.println(Arrays.toString(arr));

        radixSort(arr);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
```

---

### **Why Use Radix Sort?**
✅ **Faster than comparison-based sorting algorithms** when numbers have a limited number of digits.  
✅ **Stable sorting algorithm** (preserves the relative order of equal elements).  
✅ **Efficient for large datasets with fixed-length numbers** (e.g., ZIP codes, phone numbers).  
❌ **Only works for non-negative integers** (does not handle floating points or negatives well without modifications).  
❌ **Uses extra space** (\(O(n + k)\) due to counting sort).  

---
---
---
---


## **L I N E A R - S E A R C H**  
### **Problem Statement**  
Given an **unsorted array** and a **target value**, find the index of the target value using the **Linear Search** algorithm. If the value is not found, return **-1**.  

---

### **Real-World Example: Finding a Book in a Stack**  
Imagine you have a **stack of books** in no particular order, and you need to find a specific book. The best way is to:  
1. Start from the **first book** and check if it’s the one you need.  
2. If not, move to the **next book** and check again.  
3. Repeat this process until you find the book or reach the end of the stack.  

This is exactly how **Linear Search** works—it sequentially checks each element until it finds the target.  

---

### **Solution Explanation**  
1. **Start from the first element** of the array.  
2. **Compare each element** with the target value.  
3. If a **match is found**, return the **index**.  
4. If the loop finishes and no match is found, return **-1**.  

### **Time Complexity**  
- **Best Case:** \(O(1)\) (if the target is the first element).  
- **Worst & Average Case:** \(O(n)\) (if the target is at the end or not present).  

### **Space Complexity:** \(O(1)\) (no extra memory is used).  

---

### **Java Code Implementation (Iterative Approach)**  
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

### **Java Code Implementation (Recursive Approach)**  
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

### **Why Use Linear Search?**
✅ **Simple and easy to implement**  
✅ **Works for both sorted & unsorted arrays**  
✅ **Useful for small datasets**  
❌ **Slow for large datasets** (\(O(n)\) complexity)  
❌ **Inefficient compared to Binary Search for sorted arrays**  


---
---
---
---


## **B I N A R Y - S E A R C H**  
### **Problem Statement**  
Given a **sorted array** and a **target value**, find the index of the target using the **Binary Search** algorithm. If the value is not found, return **-1**.  

---

### **Real-World Example: Looking Up a Word in a Dictionary**  
Imagine you are searching for a word in a **dictionary**. Instead of checking page by page like **Linear Search**, you:  
1. Open the dictionary **in the middle** and check if the word is there.  
2. If the word comes **before the middle**, search in the **left half**.  
3. If the word comes **after the middle**, search in the **right half**.  
4. Repeat until you find the word or determine it's missing.  

This **divide and conquer** approach makes **Binary Search** much faster than **Linear Search**.  

---

### **Solution Explanation**  
1. **Find the middle element** of the array.  
2. Compare the middle element with the **target value**:
   - If **equal**, return the **index**.  
   - If **smaller**, search the **right half** of the array.  
   - If **larger**, search the **left half** of the array.  
3. Repeat until the target is found or the search range is empty.  

### **Time Complexity**  
- **Best Case:** \(O(1)\) (if the middle element is the target).  
- **Worst & Average Case:** \(O(\log n)\) (efficient for large datasets).  

### **Space Complexity**  
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

---
---
---
---


## **D E P T H - F I R S T - S E A R C H - (DFS)**  
### **Problem Statement**  
Given a **graph or tree**, traverse all the nodes using the **Depth First Search (DFS)** algorithm.  

DFS explores as **deep as possible** in one direction before backtracking. It can be implemented using **recursion (implicit stack)** or **iteration (explicit stack)**.  

---

### **Real-World Example: Solving a Maze**  
Imagine you are inside a **maze**, and your goal is to find the **exit**.  

1. You start at the **entrance** and choose a **random path**.  
2. You continue moving **deeper** into the maze.  
3. If you reach a **dead-end**, you backtrack to the **previous decision point** and try another path.  
4. You repeat this process until you find the **exit**.  

DFS works in a similar way—it explores a path **deeply** before backtracking.  

---

### **Solution Explanation**  
DFS is useful for problems where you need to explore all possible paths before deciding. It can be applied to both **graphs** and **trees**.  

#### **DFS Algorithm (Recursive Approach)**  
1. **Start from a node** and mark it as **visited**.  
2. **Visit all adjacent unvisited nodes**, one by one.  
3. **For each adjacent node, recursively perform DFS**.  
4. **Backtrack** when no more unvisited adjacent nodes are left.  

#### **DFS Algorithm (Iterative Approach - Using Stack)**  
1. **Push the starting node** onto a **stack**.  
2. **While the stack is not empty**:
   - Pop a node from the stack.  
   - If it’s unvisited, **mark it as visited** and push its **unvisited adjacent nodes** onto the stack.  
3. Repeat until all nodes are visited.  

### **Time Complexity**  
- **Worst, Best & Average Case:** \(O(V + E)\) (where \(V\) is the number of vertices and \(E\) is the number of edges).  

### **Space Complexity**  
- **Recursive DFS:** \(O(V)\) (due to recursive calls).  
- **Iterative DFS:** \(O(V)\) (due to stack usage).  

---

## **Java Code Implementation**  
### **DFS for Graph (Recursive Approach)**  
```java
import java.util.*;

public class DFSRecursive {
    static void dfs(Map<Integer, List<Integer>> graph, int node, Set<Integer> visited) {
        System.out.print(node + " ");
        visited.add(node);

        for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
            if (!visited.contains(neighbor)) {
                dfs(graph, neighbor, visited);
            }
        }
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        System.out.println("DFS Traversal (Recursive):");
        dfs(graph, 0, new HashSet<>());  // Start DFS from node 0
    }
}
```

---

### **DFS for Graph (Iterative Approach - Using Stack)**  
```java
import java.util.*;

public class DFSIterative {
    static void dfs(Map<Integer, List<Integer>> graph, int start) {
        Stack<Integer> stack = new Stack<>();
        Set<Integer> visited = new HashSet<>();
        
        stack.push(start);

        while (!stack.isEmpty()) {
            int node = stack.pop();
            if (!visited.contains(node)) {
                System.out.print(node + " ");
                visited.add(node);

                // Push all adjacent nodes to stack (reverse order for correct order)
                List<Integer> neighbors = graph.getOrDefault(node, new ArrayList<>());
                Collections.reverse(neighbors);
                for (int neighbor : neighbors) {
                    if (!visited.contains(neighbor)) {
                        stack.push(neighbor);
                    }
                }
            }
        }
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        System.out.println("DFS Traversal (Iterative):");
        dfs(graph, 0);  // Start DFS from node 0
    }
}
```

---

### **Why Use DFS?**
✅ **Efficient for exploring deep paths in graphs or trees**.  
✅ **Uses less memory compared to Breadth First Search (BFS)** for dense graphs.  
✅ **Can be used to detect cycles in graphs**.  
✅ **Useful for topological sorting, solving mazes, and connectivity checks**.  
❌ **Not always the shortest path (unlike BFS)**.  

---
---
---
---


## **B R E A D T H - F I R S T - S E A R C H (BFS)**  
### **Problem Statement**  
Given a **graph or tree**, traverse all the nodes using the **Breadth First Search (BFS)** algorithm.  

Unlike **Depth First Search (DFS)**, which explores **deep paths first**, BFS explores all nodes at the **current level** before moving to the next level. BFS is implemented using a **queue (FIFO - First In, First Out)**.  

---

### **Real-World Example: Finding the Shortest Path in a City**  
Imagine you are navigating a **city with interconnected roads**, and you want to find the **shortest path** to a destination.  

1. You start at the **current location (source node)**.  
2. You explore **all nearby roads (adjacent nodes)** first before moving further.  
3. Once you visit all **places at the current distance**, you move to the next level (places farther away).  
4. This ensures that the first time you reach a destination, it is via the **shortest path**.  

This **level-wise exploration** makes BFS ideal for **shortest path problems** in **unweighted graphs**.  

---

### **Solution Explanation**  
1. **Start from a given node** and mark it as **visited**.  
2. **Push it into a queue**.  
3. **While the queue is not empty**:  
   - Dequeue the front node.  
   - Visit all its **unvisited adjacent nodes** and enqueue them.  
4. Repeat until all nodes are visited.  

### **Time Complexity**  
- **Worst, Best & Average Case:** \(O(V + E)\), where \(V\) is the number of vertices and \(E\) is the number of edges.  

### **Space Complexity**  
- \(O(V)\) (for queue and visited nodes).  

---

## **Java Code Implementation**  
### **BFS for Graph (Using Queue - Iterative Approach)**  
```java
import java.util.*;

public class BFSGraph {
    static void bfs(Map<Integer, List<Integer>> graph, int start) {
        Queue<Integer> queue = new LinkedList<>();
        Set<Integer> visited = new HashSet<>();

        queue.add(start);
        visited.add(start);

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");

            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                if (!visited.contains(neighbor)) {
                    queue.add(neighbor);
                    visited.add(neighbor);
                }
            }
        }
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        System.out.println("BFS Traversal:");
        bfs(graph, 0);  // Start BFS from node 0
    }
}
```

---

### **BFS for Shortest Path in an Unweighted Graph**  
BFS can also be used to find the **shortest path** in an unweighted graph by keeping track of the distance from the source node.

```java
import java.util.*;

public class ShortestPathBFS {
    static int shortestPath(Map<Integer, List<Integer>> graph, int start, int target) {
        Queue<Integer> queue = new LinkedList<>();
        Map<Integer, Integer> distance = new HashMap<>();

        queue.add(start);
        distance.put(start, 0);

        while (!queue.isEmpty()) {
            int node = queue.poll();

            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                if (!distance.containsKey(neighbor)) {
                    queue.add(neighbor);
                    distance.put(neighbor, distance.get(node) + 1);

                    if (neighbor == target) {
                        return distance.get(neighbor);  // Found the shortest path
                    }
                }
            }
        }
        return -1;  // Target not reachable
    }

    public static void main(String[] args) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        graph.put(0, Arrays.asList(1, 2));
        graph.put(1, Arrays.asList(3, 4));
        graph.put(2, Arrays.asList(5, 6));
        graph.put(3, Arrays.asList());
        graph.put(4, Arrays.asList());
        graph.put(5, Arrays.asList());
        graph.put(6, Arrays.asList());

        int start = 0, target = 6;
        int result = shortestPath(graph, start, target);

        if (result != -1) {
            System.out.println("Shortest path from " + start + " to " + target + " is " + result);
        } else {
            System.out.println("No path found");
        }
    }
}
```

---

### **Why Use BFS?**
✅ **Finds the shortest path in an unweighted graph**.  
✅ **Best for level-wise exploration (e.g., social networks, mazes, web crawling)**.  
✅ **Guaranteed to visit each node at least once**.  
❌ **Uses more memory than DFS (queue storage)**.  

---
---
---
---

