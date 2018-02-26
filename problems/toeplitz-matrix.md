# Toeplitz Matrix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/toeplitz-matrix/description/)

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.

## My Solution
```java
class Solution {
    public boolean isToeplitzMatrix(int[][] matrix) {
        for (int i = 0; i < matrix.length - 1; i++) {
            for (int j = 0; j < matrix[i].length - 1; j++) {
                if (matrix[i][j] != matrix[i + 1][j + 1]) return false;
            }
        }
        return true;
    }
}
```

## Complexity
O(M*N)