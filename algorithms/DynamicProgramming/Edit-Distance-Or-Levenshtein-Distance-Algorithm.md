# **Edit Distance (Levenshtein Distance)**  

---

## **Problem Statement**  
Given two strings **X** and **Y**, find the **minimum number of operations** required to convert **X** into **Y**.  
The allowed operations are:  
1. **Insertion** (insert a character)  
2. **Deletion** (remove a character)  
3. **Substitution** (replace one character with another)  

### **Example**  
**Input:** `X = "kitten"`, `Y = "sitting"`  
**Output:** `Edit Distance = 3`  
**Operations:**  
1. Replace **'k'** → **'s'** → `"sitten"`  
2. Insert **'i'** → `"sittin"`  
3. Insert **'g'** → `"sitting"`  

---

## **Real-World Example: Spell Checker & Auto-Correct**  
- In search engines and word processors, **edit distance** is used to suggest corrections for misspelled words.  
- If a user types `"hte"` instead of `"the"`, the system finds `"the"` as the closest match using **Levenshtein Distance**.

---

## **Solution Explanation**  

### **1. Recursive Approach (Brute Force)**
- Try all three operations (insert, delete, substitute) for each character.
- If last characters are the same, ignore them and check the rest.
- **Time Complexity:** **\( O(3^n) \)** (exponential).

### **2. Dynamic Programming (Optimal Solution)**
- Use a **2D table `dp[i][j]`**, where:  
  - `dp[i][j]` stores the minimum edit distance between **X[0...i]** and **Y[0...j]**.  
- **Formula:**  
  \[
  dp[i][j] =
  \begin{cases} 
  dp[i-1][j-1], & \text{if } X[i] == Y[j] \\
  1 + \min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]), & \text{otherwise}
  \end{cases}
  \]  
  - **Insert:** `dp[i][j-1] + 1`  
  - **Delete:** `dp[i-1][j] + 1`  
  - **Replace:** `dp[i-1][j-1] + 1`  

- **Time Complexity:** **\( O(m \times n) \)**  
- **Space Complexity:** **\( O(m \times n) \)** (can be optimized to **\( O(n) \)**).

---

## **Java Code Implementation**  

### **1. Recursive Approach**
```java
class EditDistanceRecursive {
    public static int editDistance(String X, String Y, int m, int n) {
        if (m == 0) return n;
        if (n == 0) return m;

        if (X.charAt(m - 1) == Y.charAt(n - 1)) 
            return editDistance(X, Y, m - 1, n - 1);

        return 1 + Math.min(editDistance(X, Y, m, n - 1),  // Insert
                            Math.min(editDistance(X, Y, m - 1, n),  // Delete
                                     editDistance(X, Y, m - 1, n - 1))); // Replace
    }

    public static void main(String[] args) {
        String X = "kitten";
        String Y = "sitting";
        System.out.println("Edit Distance: " + editDistance(X, Y, X.length(), Y.length()));
    }
}
```

---

### **2. Dynamic Programming Approach (Optimized)**
```java
class EditDistanceDP {
    public static int editDistance(String X, String Y) {
        int m = X.length(), n = Y.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                if (i == 0) dp[i][j] = j;
                else if (j == 0) dp[i][j] = i;
                else if (X.charAt(i - 1) == Y.charAt(j - 1)) 
                    dp[i][j] = dp[i - 1][j - 1];
                else 
                    dp[i][j] = 1 + Math.min(dp[i - 1][j], Math.min(dp[i][j - 1], dp[i - 1][j - 1]));
            }
        }
        return dp[m][n];
    }

    public static void main(String[] args) {
        String X = "kitten";
        String Y = "sitting";
        System.out.println("Edit Distance: " + editDistance(X, Y));
    }
}
```

---

## **Why Use Edit Distance Algorithm?**  
✅ **Used in spell checking & auto-correct (Google, Microsoft Word).**  
✅ **Used in DNA sequence comparison (bioinformatics).**  
✅ **Used in plagiarism detection (finding similar texts).**  
