# **Fractional Knapsack Problem**  

---

## **Problem Statement**  
Given **N** items, each with a **weight** and **value**, determine the **maximum total value** that can be put into a knapsack of **capacity W**.  

- **Fractional Selection Allowed** → Unlike **0/1 Knapsack**, where we must take the whole item or leave it, **Fractional Knapsack** allows us to take **partial items**.  
- The goal is to **maximize total value** within the weight limit.  

---

## **Real-World Example: Gold and Silver Transport**  
A **traveler** has a **bag with weight limit** and needs to carry **valuable metals (gold, silver, platinum)**.  
- Instead of carrying **whole bars**, they can **break them into smaller pieces**.  
- They should **prioritize** carrying items with the **highest value per unit weight**.  

---

## **Solution Explanation**  
### **Greedy Algorithm Approach**  
1. **Calculate value/weight ratio** for each item.  
2. **Sort** items in **descending order** of value/weight ratio.  
3. **Pick items greedily**:  
   - Take the **whole item** if it fits.  
   - Otherwise, take a **fraction** of the item to fill the knapsack.  
4. **Stop** when the knapsack is full.  

This **greedy approach** ensures the **maximum value** is obtained.

---

## **Example**
### **Input:**  
```
Items:  [(weight=10, value=60), (weight=20, value=100), (weight=30, value=120)]
Knapsack Capacity: 50
```
### **Sorted by value/weight ratio:**
| Item  | Weight | Value | Value/Weight |
|--------|--------|--------|--------------|
| 1      | 10     | 60     | **6.0** |
| 2      | 20     | 100    | **5.0** |
| 3      | 30     | 120    | **4.0** |

### **Greedy Selection:**  
- **Take full** Item 1 (**10 kg, 60 value**)  
- **Take full** Item 2 (**20 kg, 100 value**)  
- **Take 2/3rd of** Item 3 (**20 kg of 30 kg, 80 value**)  

### **Total Value:**  
`60 + 100 + 80 = 240`

---

## **Java Code Implementation**
```java
import java.util.*;

class Item {
    int weight;
    int value;

    public Item(int weight, int value) {
        this.weight = weight;
        this.value = value;
    }
}

class FractionalKnapsack {
    public static double getMaxValue(List<Item> items, int capacity) {
        // Step 1: Sort items by value/weight ratio in descending order
        items.sort((a, b) -> Double.compare((b.value * 1.0 / b.weight), (a.value * 1.0 / a.weight)));

        double totalValue = 0.0;
        int remainingCapacity = capacity;

        // Step 2: Pick items greedily
        for (Item item : items) {
            if (item.weight <= remainingCapacity) {
                // Take full item
                totalValue += item.value;
                remainingCapacity -= item.weight;
            } else {
                // Take fractional item
                totalValue += (item.value * 1.0 / item.weight) * remainingCapacity;
                break; // Knapsack is full
            }
        }
        return totalValue;
    }

    public static void main(String[] args) {
        List<Item> items = Arrays.asList(
            new Item(10, 60),
            new Item(20, 100),
            new Item(30, 120)
        );
        int capacity = 50;

        System.out.println("Maximum Value in Knapsack = " + getMaxValue(items, capacity));
    }
}
```

---

## **Complexity Analysis**  
| Step        | Time Complexity |
|------------|----------------|
| Sorting    | **\( O(N \log N) \)** |
| Selection  | **\( O(N) \)** |
| **Total**  | **\( O(N \log N) \)** |

---

## **Why Use Fractional Knapsack?**  
✅ **Efficient for maximizing value in weight-limited scenarios**  
✅ **Used in investment portfolio selection**  
✅ **Used in supply chain optimization**  
