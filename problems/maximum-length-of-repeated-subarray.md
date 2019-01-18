# Maximum Length of Repeated Subarray - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)

## Description
Given two integer arrays A and B, return the maximum length of an subarray that appears in both arrays.

Example 1:

Input:
A: [1,2,3,2,1]

B: [3,2,1,4,7]

Output: 3

## Thinking & Notes
* Brute Force: choose one of array, e.g. A. store all A[i] into map. 
(key: A[i], value: ArrayList: store all index of occurrence of A[i]). Iterate through array B. If map contains B[i],
for each index in map ArrayList, start from the first index in list, check if B[index] == A[index]. update length.
Time: O(M∗N∗min⁡(M,N)) M,N -> length of array A and B.

* Dynamic Programming: core concept: `Whenever A[i] == B[j], we know dp[i][j] = dp[i+1][j+1] + 1`. 
This is because the position of each number in both array is adjacent.

## Solution - DP
```java
class Solution {
    public int findLength(int[] A, int[] B) {
        int res = 0;
        int[][] dp = new int[A.length+1][B.length+1];
        for (int i = A.length-1; i >= 0; i--){
            for (int j = B.length-1; j >= 0; j--){
                if (A[i] == B[j]){
                    dp[i][j] = dp[i+1][j+1] + 1;
                    if (res < dp[i][j]) res = dp[i][j];
                }
            }
        }
        return res;
    }
}
```

## Complexity
* Time Complexity:O(M∗N), where M,N are the lengths of A, B.
* Space Complexity: O(M*N)

### Core Algorithm & Data Sructure
* Dynamic Programming

### Any related or similar problems?
* [Minimum Size Subarray Sum](minimum-size-subarray-sum.md)
