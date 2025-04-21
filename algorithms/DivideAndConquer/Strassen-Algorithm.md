# **Strassen’s Algorithm for Matrix Multiplication**  

---

## **Problem Statement**  
Given two **N × N** matrices, multiply them efficiently. The **traditional** matrix multiplication algorithm has a complexity of **O(N³)**. Strassen’s algorithm reduces this to **O(Nⁿ)** with **n ≈ 2.81**, making it significantly faster for large matrices.

---

## **Real-World Example: Image Processing & Machine Learning**  
Matrix multiplication is extensively used in **computer graphics, machine learning, and scientific simulations**.  
For example, in **image processing**, **convolution operations** involve matrix multiplications, where Strassen's algorithm can speed up performance for high-resolution images.

---

## **Solution Explanation (Divide & Conquer Approach)**  
### **Traditional Matrix Multiplication**  
For two **N × N** matrices **A** and **B**, the resulting matrix **C** is computed as:  
\[
C[i][j] = \sum_{k=0}^{N-1} A[i][k] \times B[k][j]
\]
This requires **O(N³)** operations.

### **Strassen’s Approach**  
Instead of **directly computing** the product, Strassen’s Algorithm **divides** matrices into **smaller submatrices** and reduces the number of multiplications.

1. **Divide** A and B into **four equal submatrices**:  
   \[
   A = \begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix}, \quad
   B = \begin{bmatrix} B_{11} & B_{12} \\ B_{21} & B_{22} \end{bmatrix}
   \]

2. **Compute 7 intermediate products** instead of 8 using:**  
   \[
   \begin{aligned}
   M_1 &= (A_{11} + A_{22}) (B_{11} + B_{22}) \\
   M_2 &= (A_{21} + A_{22}) B_{11} \\
   M_3 &= A_{11} (B_{12} - B_{22}) \\
   M_4 &= A_{22} (B_{21} - B_{11}) \\
   M_5 &= (A_{11} + A_{12}) B_{22} \\
   M_6 &= (A_{21} - A_{11}) (B_{11} + B_{12}) \\
   M_7 &= (A_{12} - A_{22}) (B_{21} + B_{22}) \\
   \end{aligned}
   \]

3. **Compute the final quadrants of matrix C:**  
   \[
   \begin{aligned}
   C_{11} &= M_1 + M_4 - M_5 + M_7 \\
   C_{12} &= M_3 + M_5 \\
   C_{21} &= M_2 + M_4 \\
   C_{22} &= M_1 - M_2 + M_3 + M_6 \\
   \end{aligned}
   \]

---

## **Example Calculation**  
### **Input Matrices**  
\[
A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad
B = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
\]

### **Computation (Using Strassen's Formula)**
\[
M_1 = (1+4)(5+8) = 5 \times 13 = 65
\]
\[
M_2 = (3+4) \times 5 = 7 \times 5 = 35
\]
\[
M_3 = 1 \times (6-8) = 1 \times (-2) = -2
\]
\[
M_4 = 4 \times (7-5) = 4 \times 2 = 8
\]
\[
M_5 = (1+2) \times 8 = 3 \times 8 = 24
\]
\[
M_6 = (3-1) \times (5+6) = 2 \times 11 = 22
\]
\[
M_7 = (2-4) \times (7+8) = (-2) \times 15 = -30
\]

### **Final Matrix C**
\[
C_{11} = 65 + 8 - 24 - 30 = 19
\]
\[
C_{12} = -2 + 24 = 22
\]
\[
C_{21} = 35 + 8 = 43
\]
\[
C_{22} = 65 - 35 - 2 + 22 = 50
\]

### **Final Output Matrix**
\[
C = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
\]

---

## **Java Code Implementation**
```java
import java.util.Arrays;

public class StrassenMatrixMultiplication {
    public static int[][] multiply(int[][] A, int[][] B) {
        int n = A.length;
        if (n == 1) {
            return new int[][]{{A[0][0] * B[0][0]}};
        }

        int newSize = n / 2;
        int[][] A11 = new int[newSize][newSize];
        int[][] A12 = new int[newSize][newSize];
        int[][] A21 = new int[newSize][newSize];
        int[][] A22 = new int[newSize][newSize];

        int[][] B11 = new int[newSize][newSize];
        int[][] B12 = new int[newSize][newSize];
        int[][] B21 = new int[newSize][newSize];
        int[][] B22 = new int[newSize][newSize];

        splitMatrix(A, A11, 0, 0);
        splitMatrix(A, A12, 0, newSize);
        splitMatrix(A, A21, newSize, 0);
        splitMatrix(A, A22, newSize, newSize);

        splitMatrix(B, B11, 0, 0);
        splitMatrix(B, B12, 0, newSize);
        splitMatrix(B, B21, newSize, 0);
        splitMatrix(B, B22, newSize, newSize);

        int[][] M1 = multiply(add(A11, A22), add(B11, B22));
        int[][] M2 = multiply(add(A21, A22), B11);
        int[][] M3 = multiply(A11, subtract(B12, B22));
        int[][] M4 = multiply(A22, subtract(B21, B11));
        int[][] M5 = multiply(add(A11, A12), B22);
        int[][] M6 = multiply(subtract(A21, A11), add(B11, B12));
        int[][] M7 = multiply(subtract(A12, A22), add(B21, B22));

        int[][] C11 = add(subtract(add(M1, M4), M5), M7);
        int[][] C12 = add(M3, M5);
        int[][] C21 = add(M2, M4);
        int[][] C22 = add(subtract(add(M1, M3), M2), M6);

        int[][] C = new int[n][n];
        joinMatrix(C, C11, 0, 0);
        joinMatrix(C, C12, 0, newSize);
        joinMatrix(C, C21, newSize, 0);
        joinMatrix(C, C22, newSize, newSize);

        return C;
    }

    private static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] result = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                result[i][j] = A[i][j] + B[i][j];
        return result;
    }

    private static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] result = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                result[i][j] = A[i][j] - B[i][j];
        return result;
    }

    public static void main(String[] args) {
        int[][] A = {{1, 2}, {3, 4}};
        int[][] B = {{5, 6}, {7, 8}};
        int[][] result = multiply(A, B);
        System.out.println(Arrays.deepToString(result));
    }
}
```

---

## **Time Complexity Analysis**  
| Step           | Complexity |
|---------------|------------|
| Matrix division | **O(1)** |
| Recursive calls | **O(N².81)** |
| **Total** | **O(N².81)** |

---

