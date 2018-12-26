# Contains Duplicate II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/contains-duplicate-ii/)

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

Example 1:

Input: nums = [1,2,3,1], k = 3

Output: true

## My Solution
```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        if (nums == null) return false;
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        for (int i = 0; i < nums.length; i++){
            if (map.containsKey(nums[i])){
                if ((i - map.get(nums[i])) <= k) return true;
                map.put(nums[i], i);
            } else {
                map.put(nums[i], i);
            }
        }
        return false;
    }
}
```
