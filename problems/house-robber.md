# House Robber - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/house-robber/)

## Description
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

## Thinking & Notes
* Recursion Brute force: 
  - A robber has 2 options: 
    - rob current house i; 
    - don't rob current house.
  - If an option `a` is selected it means she can't rob previous `i-1` house but can safely proceed to the one before previous `i-2` and gets all cumulative loot that follows.
  - If an option `b` is selected the robber gets all the possible loot from robbery of `i-1` and all the following buildings.
  - So it boils down to calculating what is more profitable:
    - robbery of current house + loot from houses before the previous
    - loot from the previous house robbery and any loot captured before that
  - `rob(i) = Math.max( rob(i - 2) + currentHouseValue, rob(i - 1) )`

* Recursion with `mem`
  - to improve the brute force approach, we can introduce an array to store calculated results.

* Iterative + memo (bottom-up)
  - same idea.

* Iterative + variable
  - We can notice that in the previous step we use only memo[i] and memo[i-1], so going just 2 steps back. We can hold them in 2 variables instead. This optimization is met in Fibonacci sequence creation 

## Solution - Recursion Brute force - Time Limit Exceeded
```java
class Solution {
    public int rob(int[] nums) {
        return helper(nums.length-1, nums);
    }
    
    private int helper(int i, int[] nums){
        if (i < 0) return 0;
        return Math.max(helper(i - 1, nums), helper(i - 2, nums) + nums[i]);
    }
}
```
#### Complexity
* Time Complexity: O(2^n)?
* Space Complexity: O(1)

## Solution - Recursion with `mem`
```java
class Solution {
    public int rob(int[] nums) {
        int[] mem = new int[nums.length];
        Arrays.fill(mem, -1);
        return helper(nums.length-1, nums, mem);
    }
    
    private int helper(int i, int[] nums, int[] mem){
        if (i < 0) return 0;
        if (mem[i] >= 0) return mem[i];
        mem[i] = Math.max(helper(i - 1, nums, mem), helper(i - 2, nums, mem) + nums[i]);
        return mem[i];
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

## Solution - Iterative + memo (bottom-up)
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 0) return 0;
        int[] mem = new int[nums.length+1];
        mem[0] = 0;
        mem[1] = nums[0];
        
        for (int i = 1; i < nums.length; i++){
            mem[i+1] = Math.max(mem[i], mem[i - 1] + nums[i]);
        }
        return mem[nums.length];
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

## Solution - Iterative + variable
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 0) return 0;
        int prev1 = 0, prev2 = 0;
        // order: prev1, prev2, n
        for (int n : nums){
            int tmp = prev2;
            prev2 = Math.max(prev2, prev1 + n);
            prev1 = tmp;
        }
        return prev2;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
