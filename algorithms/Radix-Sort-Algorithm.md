# **R A D I X - S O R T**  
## **Problem Statement**  
Given an array of **non-negative integers**, sort it in **ascending order** using the **Radix Sort** algorithm.  

---

## **Real-World Example: Sorting Mail by ZIP Code**  
Imagine you work at a **postal service** and need to **sort mail** based on ZIP codes. You can’t compare all ZIP codes at once, so you:  
1. Sort letters based on the **last digit** of the ZIP code.  
2. Sort again based on the **second last digit**.  
3. Continue this process until the ZIP codes are completely sorted.  

This is exactly how **Radix Sort** works! It sorts numbers **digit by digit**, starting from the least significant digit (LSD).  

---

## **Solution Explanation**  
Radix Sort works by sorting numbers based on individual digits, starting from the **least significant digit (LSD)** to the **most significant digit (MSD)**.  

### **Steps to Perform Radix Sort:**  
1. **Find the maximum number** in the array to determine the number of digits.  
2. **Sort numbers digit by digit** using a **stable sorting algorithm** (usually **Counting Sort**).  
3. **Repeat for each digit**, moving from the **least significant digit (LSD)** to the **most significant digit (MSD)**.  
4. Once all digits are processed, the array becomes sorted.  

### **Time Complexity**  
- **Best, Average & Worst Case:** \(O(nk)\) (where \(n\) is the number of elements and \(k\) is the maximum number of digits).  
- **Space Complexity:** \(O(n + k)\) (due to extra space in Counting Sort).  

---

## **Java Code Implementation**  
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

## **Why Use Radix Sort?**
✅ **Faster than comparison-based sorting algorithms** when numbers have a limited number of digits.  
✅ **Stable sorting algorithm** (preserves the relative order of equal elements).  
✅ **Efficient for large datasets with fixed-length numbers** (e.g., ZIP codes, phone numbers).  
❌ **Only works for non-negative integers** (does not handle floating points or negatives well without modifications).  
❌ **Uses extra space** (\(O(n + k)\) due to counting sort).  
