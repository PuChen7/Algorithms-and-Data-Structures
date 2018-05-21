# Maximum Subarray - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/maximum-subarray/description/)

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example:

Input: [-2,1,-3,4,-1,2,1,-5,4],

Output: 6

Explanation: [4,-1,2,1] has the largest sum = 6.

## Solution - Kadane’s Algorithm
```java
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums == null) return 0;
        // max_tmp hold the tmp sum, max_res holds the max so far
        int max_tmp = nums[0], max_res = nums[0];  
        
        for (int i = 1; i < nums.length; i++){
            max_tmp = Math.max(nums[i], max_tmp+nums[i]);
            max_res = Math.max(max_tmp, max_res);
        }
        return max_res;
    }
}
```
### Complexity
Time Complexity: O(n) - only go over the array once