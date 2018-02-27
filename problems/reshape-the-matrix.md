# Reshape the Matrix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reshape-the-matrix/description/)

You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

## My Solution
```java
class Solution {
    public int[][] matrixReshape(int[][] nums, int r, int c) {
        if (nums.length*nums[0].length != r*c)
            return nums;
        
        int[][] res = new int[r][c];
        int row = 0;
        int col = 0;
        for (int i = 0; i < r; i++){
            for (int j = 0; j < c; j++){
                if (col == nums[0].length){
                    col = 0;
                    row += 1;
                }
                res[i][j] = nums[row][col];
                col += 1;
            }
        }
        return res;
    }
}
```

## Complexity
O(M*N)