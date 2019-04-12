# Search a 2D Matrix II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-a-2d-matrix-ii/)

## Description
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
* Integers in each row are sorted in ascending from left to right.
* Integers in each column are sorted in ascending from top to bottom.

## Thinking & Notes
* start from right corner. if target < matrix[i] -> col--, if target > matrix[i] -> row++

## Solution
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length < 1 || matrix[0].length < 1) return false;
        int row = 0, col = matrix[0].length-1;
        while (row < matrix.length && col >= 0) {
            if (target == matrix[row][col]) return true;
            else if (target < matrix[row][col]) col--;
            else row++;
        }
        return false;
    }
}
```

### Complexity
* Time Complexity: O(m+n)
* Space Complexity: O(1)
