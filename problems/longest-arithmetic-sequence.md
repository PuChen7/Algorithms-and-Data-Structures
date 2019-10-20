# Longest Arithmetic Sequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-arithmetic-sequence/)

## Description
Given an array A of integers, return the length of the longest arithmetic subsequence in A.

Recall that a subsequence of A is a list A[i_1], A[i_2], ..., A[i_k] with 0 <= i_1 < i_2 < ... < i_k <= A.length - 1, and that a sequence B is arithmetic if B[i+1] - B[i] are all the same value (for 0 <= i < B.length - 1).

## Thinking & Notes
* DP: 
  - use `array of Map` to store diff
  - take each number as a end, `nums[i]` and create a Map at `nums[i]`
  - keep check the current seq, and update map at `nums[i]`

## Solution - DP
```java
class Solution {
    public int longestArithSeqLength(int[] A) {
        HashMap<Integer, Integer>[] dp = new HashMap[A.length];
        int res = 0;
        for (int i = 0; i < A.length; i++){
            dp[i] = new HashMap<>();
            for (int j = 0; j < i; j++){
                // take each number as the end of the seq
                // use map to count all diff
                // NOTE: the diff is the diff btw A[i] and every A[j]
                // keep updating the end number's map
                int diff = A[i] - A[j];
                // dp[i] is a new map, we get diff with j, then look up in j's map,
                // what we found in j's map is the longest length of this diff with end as j
                dp[i].put(diff, dp[j].getOrDefault(diff, 1) + 1);
                res = Math.max(res, dp[i].get(diff));
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n^2)
