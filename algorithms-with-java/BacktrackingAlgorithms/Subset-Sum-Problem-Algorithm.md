Sure! Let's dive into the **Subset Sum Problem**, which is a classic **Dynamic Programming** and **Backtracking** problem, often used to teach optimization and decision-making under constraints.

---

## 🧩 **Problem Statement: Subset Sum Problem**

You are given a set (or array) of **positive integers** and a **target sum**.

🔍 Your task is to **determine whether there is a subset** of the given set whose elements **sum up to the target**.

---

## 🌍 **Real-World Analogy**

Imagine you're shopping with a fixed amount of money (target sum), and you have a list of item prices (array). You want to know **whether you can pick a combination of items** such that **the total cost is exactly equal** to the money you have — not less, not more.

---

## 💡 **Solution Approaches**

### ✅ 1. **Recursive (Brute Force) Approach**
Try all subsets recursively:
- For each number, you have two choices: **include it** or **exclude it**.
- Recursively check both cases.
- If any path results in the target sum, return `true`.

**Time Complexity:** `O(2^n)` – because there are 2 choices for each element (include/exclude)

---

### ✅ 2. **Dynamic Programming (Top-Down / Bottom-Up)**

We use a 2D boolean table `dp[i][j]` which is `true` if a **subset of the first `i` elements** can make sum `j`.

**Transition Formula:**

```
dp[i][j] = dp[i-1][j] || dp[i-1][j - arr[i-1]]
```

- `dp[i-1][j]`: Exclude current element.
- `dp[i-1][j - arr[i-1]]`: Include current element (if it's not greater than `j`).

---

## 🧪 **Example**

```text
Input:
arr = {3, 34, 4, 12, 5, 2}
target sum = 9

Output:
true
Explanation: Subset {4, 5} sums to 9
```

---

## 🔧 **Java Code (Dynamic Programming - Bottom-Up)**

```java
public class SubsetSum {

    public static boolean isSubsetSum(int[] arr, int target) {
        int n = arr.length;
        boolean[][] dp = new boolean[n + 1][target + 1];

        // Initialize first column as true (sum 0 can always be made with empty subset)
        for (int i = 0; i <= n; i++)
            dp[i][0] = true;

        // Initialize first row, except dp[0][0], as false
        for (int j = 1; j <= target; j++)
            dp[0][j] = false;

        // Fill the subset table
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= target; j++) {
                if (arr[i - 1] > j)
                    dp[i][j] = dp[i - 1][j]; // can't include the current element
                else
                    dp[i][j] = dp[i - 1][j] || dp[i - 1][j - arr[i - 1]];
            }
        }

        return dp[n][target];
    }

    public static void main(String[] args) {
        int[] arr = {3, 34, 4, 12, 5, 2};
        int target = 9;

        if (isSubsetSum(arr, target))
            System.out.println("Subset with the given sum exists.");
        else
            System.out.println("No subset with the given sum found.");
    }
}
```

---

## ⏱️ **Time and Space Complexity**

| Type              | Complexity          |
|-------------------|---------------------|
| Time Complexity    | `O(n * target)`     |
| Space Complexity   | `O(n * target)`     |

*You can optimize space to O(target) using a 1D array if needed.*

---

## 🧠 Summary

| Aspect             | Description                            |
|--------------------|----------------------------------------|
| Problem Type        | Decision Problem (Subset of Set)       |
| Core Concept        | Backtracking / DP                      |
| Goal                | Find subset summing to target          |
| Real World          | Budget planning, shopping with limits  |
| Best Approach       | Dynamic Programming (Bottom-Up)        |

---

