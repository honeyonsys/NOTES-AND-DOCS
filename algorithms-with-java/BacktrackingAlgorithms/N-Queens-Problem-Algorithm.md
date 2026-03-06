Sure! Let's dive into the **N-Queens Problem**—a classic backtracking algorithm problem that's often asked in coding interviews and competitive programming.

---

## 🧩 **Problem Statement: N-Queens Problem**

You are given a chessboard of size **N x N**. The goal is to **place N queens on the board** such that **no two queens threaten each other**.

A queen can move:
- Horizontally (same row)
- Vertically (same column)
- Diagonally (both directions)

You must place all N queens so that none can attack another.

---

## 🌍 **Real-World Analogy**

Think of organizing N high-ranking officials (queens) in a palace (the chessboard), where each one demands **privacy and security**. No one should be in the same row, column, or diagonal path—just like having their own protected floor, hallway, and corner view.

---

## 💡 **Solution Explanation: Using Backtracking**

### Approach:
1. Place a queen in the **first row**.
2. Try placing the next queen in a **valid column** of the next row.
3. If there is no valid column (conflict), **backtrack** to the previous row and move the previous queen to the next column.
4. Continue until **N queens** are placed or all options are exhausted.

We use a **recursive function** to try placing queens **row by row**.

### Valid Placement:
A position is valid if:
- There is **no other queen in the same column**.
- There is **no queen on either diagonal**.

---

## ✅ **Example: 4-Queens Problem**

Place 4 queens on a 4×4 board.

### One valid solution:
```
. Q . .
. . . Q
Q . . .
. . Q .
```

---

## 🧪 **Java Code Implementation**

```java
public class NQueens {

    static int N = 4;

    public static void main(String[] args) {
        char[][] board = new char[N][N];
        
        // Initialize the board with '.'
        for (int i = 0; i < N; i++)
            for (int j = 0; j < N; j++)
                board[i][j] = '.';

        solveNQueens(board, 0);
    }

    static boolean isSafe(char[][] board, int row, int col) {
        // Check column
        for (int i = 0; i < row; i++)
            if (board[i][col] == 'Q')
                return false;

        // Check upper-left diagonal
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 'Q')
                return false;

        // Check upper-right diagonal
        for (int i = row, j = col; i >= 0 && j < N; i--, j++)
            if (board[i][j] == 'Q')
                return false;

        return true;
    }

    static void solveNQueens(char[][] board, int row) {
        if (row == N) {
            printBoard(board);
            return;
        }

        for (int col = 0; col < N; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 'Q';
                solveNQueens(board, row + 1); // Recursively place next queen
                board[row][col] = '.'; // Backtrack
            }
        }
    }

    static void printBoard(char[][] board) {
        System.out.println("---- Solution ----");
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++)
                System.out.print(board[i][j] + " ");
            System.out.println();
        }
    }
}
```

---

## ⏱️ **Time Complexity**

- **Worst-case time complexity:** `O(N!)`
  - Because in the worst case, we might try all permutations of queens in rows.

- **Space complexity:** `O(N²)` if we store the board.

---

## 🔁 Summary

| Aspect         | Detail                                   |
|----------------|------------------------------------------|
| Problem Type   | Backtracking                             |
| Goal           | Place N queens with no conflicts         |
| Strategy       | Try & backtrack                          |
| Time Complexity| O(N!)                                    |
| Real World     | Privacy/security layout problem          |

---

