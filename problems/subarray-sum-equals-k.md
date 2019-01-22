# Subarray Sum Equals K - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/subarray-sum-equals-k/)

## Description
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1:

Input:nums = [1,1,1], k = 2

Output: 2

## Thinking & Notes
* Brute Force: iterate array with two for loops. check every subarray.
* HashMap with pre-sum: we know the key to solve this problem is `SUM[i, j]`. So if we know `SUM[0, i - 1]` and `SUM[0, j]`, 
then we can easily get `SUM[i, j]`.

## Solution - Brute Force
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int res = 0;
        for (int i = 0; i < nums.length; i++){
            int sum = 0;
            for (int j = i; j < nums.length; j++){
                sum += nums[j];
                if (sum == k) res++;
            }
        }
        return res;
    }
}
```
### Complexity
* Time: O(n^2)
* Space: O(1)

## Solution - HashMap
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int res = 0;
        int sum = 0;
        for (int i = 0; i < nums.length; i++){
            sum += nums[i];
            if (map.containsKey(sum - k)) res += map.get(sum - k);
            map.put(sum, map.getOrDefault(sum, 0)+1);
        }
        return res;
    }
}
```
### Complexity
* Time: O(n)
* Space: O(n)
