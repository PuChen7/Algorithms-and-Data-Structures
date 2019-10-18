# Longest Increasing Subsequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-increasing-subsequence/)

## Description
Given an unsorted array of integers, find the length of longest increasing subsequence.

## Thinking & Notes
* Brute Force: 
    - consider two cases:
        - include current position
        - not include current position
* Dynamic Programming: use an array to store current longest subarray at each index.
    - take each digit as the end of the sequence, find the longest subsequence of current sequence.
    - only update if the previous +1 is greater
        - if not greater, it means at this index, this number (a) has at least 1 number (b) that `b > a` which doesn't satisfy increasing order, so it doesn't update. 
* Binary Search: use `patience sort` to form tails.

## Solution - Brute Force - TLE
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        return helper(nums, 0, Integer.MIN_VALUE);
    }
    
    private int helper(int[] nums, int curr, int prev){
        if (curr == nums.length) return 0;
        int include = 0;
        if (nums[curr] > prev)
            include = 1 + helper(nums, curr+1, nums[curr]);
        int exclude = helper(nums, curr + 1, prev);
        return Math.max(include, exclude);
    }
}
```
### Complexity
* Time Complexity: O(2^n)
* Space Complexity: O(n) 
    * why space complexity is O(n)?
        - Our memory complexity is determined by the number of return statements because each function call will be stored on the program stack. To generalize, a recursive function's memory complexity is O(recursion depth). As our tree depth suggests, we will have n total return statements and thus the memory complexity is O(n).

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

## Solution - Binary Search
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] tails = new int[nums.length];
        int size = 0;
        for (int num : nums) {
            int i = 0, j = size;
            while (i != j) {
                int m = (i+j) / 2;
                if (num > tails[m])
                    i = m + 1;
                else 
                    j = m;
            }
            tails[i] = num;
            if (i == size) size++;
        }
        return size;
    }
}
```
### Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(n)
