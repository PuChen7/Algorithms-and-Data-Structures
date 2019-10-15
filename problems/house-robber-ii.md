# House Robber II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/house-robber-ii/)

## Description
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

## Thinking & Notes
* Dynamic Programming: 
  - Think of diff cases: suppose there are `10` houses: `[0...n]`
    1. case 1: rob 0, leave n
    2. case 2: leave 0, rob n
    3. case 3: leave both - this case can be covered by case 1 & 2. 

## Solution - Dynamic Programming
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) return nums[0];  
        return Math.max(rob1(nums), rob2(nums));
    }
    
    // case 1: rob 0, leave n
    private int rob1(int[] nums){
        int prev = 0, mid = 0;
        for (int i = 0; i < nums.length - 1; i++){
            int tmp = mid;
            mid = Math.max(mid, prev + nums[i]);
            prev = tmp;
        }
        return mid;
    }
    
    // case 2: leave 0, rob n
    private int rob2(int[] nums){
        int prev = 0, mid = 0;
        for (int i = 1; i < nums.length; i++){
            int tmp = mid;
            mid = Math.max(mid, prev + nums[i]);
            prev = tmp;
        }
        return mid;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Dynamic Programming - revised to one method
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) return nums[0];
        return Math.max(robHelper(nums, 0, nums.length - 1), robHelper(nums, 1, nums.length));
    }
    
    private int robHelper(int[] nums, int start, int end){
        int prev = 0, mid = 0;
        for (int i = start; i < end; i++){
            int tmp = mid;
            mid = Math.max(mid, prev + nums[i]);
            prev = tmp;
        }
        return mid;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
