# Minimum Size Subarray Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/minimum-size-subarray-sum/)

## Description
Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.

Example: 

Input: s = 7, nums = [2,3,1,2,4,3]

Output: 2

## Thinking & Notes
* Brute Force: check every sub array.

## Solution - Brute Force
```java
class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        int res = Integer.MAX_VALUE;
        int sum = 0;
        for (int i = 0; i < nums.length; i++){
            for (int j = i; j < nums.length; j++){
                sum += nums[j];
                if (sum >= s){
                    res = Math.min((j-i+1), res);
                    break;
                }
            }
            sum = 0;
        }
        return res == Integer.MAX_VALUE ? 0 : res;
    }
}
```
### Complexity
* Time Complexity: O(n^3)
* Space Complexity: O(1)
