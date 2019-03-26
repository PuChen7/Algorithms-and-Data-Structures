# Search a 2D Matrix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-a-2d-matrix/)

## Description
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

## Thinking & Notes
- Brute force: search the entire matrix. two for loops. O(n)
- Think as sorted list: modify matrix index. `matrix[mid/col][mid%col] == target`

## Solution - Brute force
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        for (int i = 0; i < matrix.length; i++){
            for (int j = 0; j < matrix[i].length; j++){
                if (matrix[i][j] == target) return true;
            }
        }
        return false;
    }
}
```
### Complexity
* Time Complexity: O(n*m)
* Space Complexity: O(1)

## Solu8tion - Think as sorted list
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0) return false;
        int lo = 0, hi = matrix.length * matrix[0].length - 1, col = matrix[0].length;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (matrix[mid/col][mid%col] == target) return true;
            else if (matrix[mid/col][mid%col] < target) lo = mid + 1;
            else hi = mid - 1;
        }
        return false;
    }
}
```
### Complexity
* Time Complexity: O(log(n*m))
* Space Complexity: O(1)
