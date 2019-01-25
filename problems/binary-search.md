# Binary Search - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-search/)

## Description
Given a sorted (in ascending order) integer array nums of n elements and a target value, write a function to search target in nums. If target exists, then return its index, otherwise return -1.

## Thinking & Notes
* Typical approach: binary search with `while loop`

## Solution - Typical approach
```java
class Solution {
    public int search(int[] nums, int target) {
        int lo = 0, hi = nums.length-1;
        while (lo <= hi){
            int mid = lo + (hi - lo) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] > target) hi = mid - 1;
            else lo = mid + 1;
        }
        return -1;
    }
}
```

### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)

### Core Algorithm & Data Sructure
* Binary Search
