# Search in Rotated Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## Description
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

## Thinking & Notes
* Modified Binary Search: 
  1. find the smallest value. 
  2. do normal binary search, mid need to recalculate by `(smallestVleIndex + mid)/2`

## Solution - Modified Binary Search
```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums == null) return -1;
        int lo = 0, hi = nums.length - 1;
        while (lo < hi){
            int mid = (lo + hi)/2;
            if (nums[mid] > nums[hi]) lo = mid + 1;
            else hi = mid;
        }
        
        int minVle = lo;
        hi = nums.length - 1;
        lo = 0;
        while (lo <= hi){
            int mid = (lo+hi) / 2;
            int realMid = (minVle + mid) % nums.length;
            if (nums[realMid] == target) return realMid;
            else if (nums[realMid] > target) hi = mid - 1;
            else lo = mid + 1;
        }
        return -1;
    }
}
```

### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)
