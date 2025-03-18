# **Activity Selection Problem**  

---

## **Problem Statement**  
Given **N** activities, each with a **start time** and **end time**, select the **maximum number of activities** that can be performed **without overlapping**.  

### **Constraints**  
- Only **one activity** can be performed at a time.  
- Activities are represented as **(start, end)** pairs.  

---

### **Example**  
#### **Input:**  
```
Activities: [(1, 3), (2, 5), (4, 6), (6, 8), (5, 7), (8, 9)]
```
#### **Output:**  
```
Maximum activities: [(1, 3), (4, 6), (6, 8), (8, 9)]
```
Total **4** activities are selected.

---

## **Real-World Example: Scheduling Meetings in a Conference Room**  
A company has a single **conference room** and multiple meetings to schedule. The goal is to **maximize** the number of meetings without overlapping times.  
- Meetings are activities.  
- The **end time of one meeting must not overlap** with the **start time of the next meeting**.  
- The **optimal solution** ensures the room is **utilized efficiently**.

---

## **Solution Explanation**  
### **Greedy Algorithm Approach**  
1. **Sort** all activities by their **end times** (earliest finishing first).  
2. **Select the first activity** (since it ends the earliest).  
3. For each remaining activity:  
   - If the **start time** is **greater than or equal to** the previous **end time**, select it.  
4. Repeat until all activities are checked.  

This **greedy approach** ensures maximum non-overlapping activities are selected.

---

## **Java Code Implementation**
```java
import java.util.*;

class Activity {
    int start, end;

    public Activity(int start, int end) {
        this.start = start;
        this.end = end;
    }
}

public class ActivitySelection {
    public static void selectActivities(List<Activity> activities) {
        // Step 1: Sort activities by end time
        activities.sort(Comparator.comparingInt(a -> a.end));

        System.out.println("Selected activities:");

        // Step 2: Select the first activity
        int lastEndTime = activities.get(0).end;
        System.out.println("(" + activities.get(0).start + ", " + activities.get(0).end + ")");

        // Step 3: Iterate and select non-overlapping activities
        for (int i = 1; i < activities.size(); i++) {
            if (activities.get(i).start >= lastEndTime) {
                System.out.println("(" + activities.get(i).start + ", " + activities.get(i).end + ")");
                lastEndTime = activities.get(i).end;
            }
        }
    }

    public static void main(String[] args) {
        List<Activity> activities = Arrays.asList(
            new Activity(1, 3),
            new Activity(2, 5),
            new Activity(4, 6),
            new Activity(6, 8),
            new Activity(5, 7),
            new Activity(8, 9)
        );

        selectActivities(activities);
    }
}
```

---

## **Complexity Analysis**  
| Step            | Time Complexity |
|----------------|----------------|
| Sorting        | **\( O(N \log N) \)** |
| Activity Selection | **\( O(N) \)** |
| **Total**      | **\( O(N \log N) \)** |

---

## **Why Use Activity Selection?**  
✅ **Used in scheduling meetings, lectures, and tasks**  
✅ **Ensures optimal resource utilization**  
✅ **Efficient (greedy approach gives an optimal solution)**  
