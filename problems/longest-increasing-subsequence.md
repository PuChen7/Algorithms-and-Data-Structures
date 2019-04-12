# Longest Increasing Subsequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-increasing-subsequence/)

## Description
Given an unsorted array of integers, find the length of longest increasing subsequence.

## Thinking & Notes
* Dynamic Programming: use an array to store current longest subarray at each index.

## Solution - Dynamic Programming
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int[] arr = new int[nums.length];
        for (int i = 0; i < arr.length; i++)
            arr[i] = 1;
        
        for (int i = 1; i < nums.length; i++){
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    if (arr[j] + 1 > arr[i])
                        arr[i] = arr[j] + 1;
                }
            }
        }
        
        int res = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++)
            res = Math.max(res, arr[i]);
        return res;
    }
}
```

### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n)
