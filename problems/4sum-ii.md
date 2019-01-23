# 4Sum II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/4sum-ii/)

## Description
Given four lists A, B, C, D of integer values, compute how many tuples (i, j, k, l) there are such that A[i] + B[j] + C[k] + D[l] is zero.

To make problem a bit easier, all A, B, C, D have same length of N where 0 ≤ N ≤ 500. All integers are in the range of -228 to 228 - 1 and the result is guaranteed to be at most 231 - 1.

Example:

Input:
A = [ 1, 2]
B = [-2,-1]
C = [-1, 2]
D = [ 0, 2]

Output:
2

## Thinking & Notes
* HashMap: do sum seperately. 

## Solution - HashMap
```java
class Solution {
    public int fourSumCount(int[] A, int[] B, int[] C, int[] D) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < A.length; i++){
            for (int j = 0; j < B.length; j++){
                int sum = A[i] + B[j];
                map.put(sum, map.getOrDefault(sum, 0)+1);
            }
        }
        
        int res = 0;
        for (int i = 0; i < C.length; i++){
            for (int j = 0; j < D.length; j++){
                res += map.getOrDefault(-1 * (C[i] + D[j]), 0);
            }
        }
        return res;
    }
}
```

### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n)
