# **Longest Common Subsequence (LCS)**  

---

## **Problem Statement**  
Given two sequences, **find the length of the longest subsequence** present in both of them.  
A **subsequence** is a sequence derived from another sequence by **deleting some or no elements without changing the order of the remaining elements**.  

---

## **Real-World Example: DNA Sequence Matching**  
In **bioinformatics**, DNA sequences are compared to find similarities.  
For example, if we have two DNA sequences:  
- **X = "ACGTGTC"**  
- **Y = "ACTTGC"**  

The **LCS = "ACTGC"** (length = 5) represents the **longest matching pattern** in both sequences.

---

## **Solution Explanation**  

### **1. Recursive Approach (Brute Force)**
- Compare last characters of both strings:
  - If **same**, include it in LCS and check for remaining substring.
  - If **different**, find LCS by **excluding** one character at a time.  
- **Time Complexity**: **\( O(2^n) \)** (exponential).  

### **2. Dynamic Programming (Optimal Solution)**
- Use a **2D table** `dp[i][j]` to store LCS values.  
- **Formula:**  
  \[
  dp[i][j] =
  \begin{cases} 
  1 + dp[i-1][j-1], & \text{if } X[i] == Y[j] \\
  \max(dp[i-1][j], dp[i][j-1]), & \text{otherwise}
  \end{cases}
  \]  
- **Time Complexity**: **\( O(m \times n) \)** (polynomial).  
- **Space Complexity**: **\( O(m \times n) \)** (can be optimized to **\( O(n) \)**).

---

## **Java Code Implementation**

### **1. Recursive Approach**
```java
class LCSRecursive {
    public static int lcs(String X, String Y, int m, int n) {
        if (m == 0 || n == 0) return 0;
        if (X.charAt(m - 1) == Y.charAt(n - 1)) 
            return 1 + lcs(X, Y, m - 1, n - 1);
        else 
            return Math.max(lcs(X, Y, m - 1, n), lcs(X, Y, m, n - 1));
    }

    public static void main(String[] args) {
        String X = "ACGTGTC";
        String Y = "ACTTGC";
        System.out.println("Length of LCS: " + lcs(X, Y, X.length(), Y.length()));
    }
}
```

---

### **2. Dynamic Programming Approach (Optimized)**
```java
class LCSDP {
    public static int lcs(String X, String Y) {
        int m = X.length(), n = Y.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (X.charAt(i - 1) == Y.charAt(j - 1)) 
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                else 
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
        return dp[m][n];
    }

    public static void main(String[] args) {
        String X = "ACGTGTC";
        String Y = "ACTTGC";
        System.out.println("Length of LCS: " + lcs(X, Y));
    }
}
```

---

## **Why Use LCS Algorithm?**  
✅ **Used in DNA sequence alignment (bioinformatics).**  
✅ **Used in file comparison tools (like Git diff, text editors).**  
✅ **Used in plagiarism detection (checking similarity of texts).**  
