# Search in Rotated Sorted Array II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

## Description
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,0,1,2,2,5,6] might become [2,5,6,0,0,1,2]).

You are given a target value to search. If found in the array return true, otherwise return false.

## Thinking & Notes
* Binary Search (check two sides): determine which side is sorted based on `mid`, then check if target is in this range, move `hi` or `lo`.
* Binary Search (check one sides): determine which side is sorted, no need to check two parts.

## Solution - Binary Search (check two sides)
```java
class Solution {
    public boolean search(int[] nums, int target) {
        int lo = 0, hi = nums.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (target == nums[mid]) return true;
            else if (nums[mid] > nums[lo] || nums[mid] > nums[hi]) { // left side is sorted
                if (target >= nums[lo] && target < nums[mid]){
                    hi = mid - 1;
                } else {
                    lo = mid + 1;
                }
            } else if (nums[mid] < nums[lo] || nums[mid] < nums[hi]){ // right side is sorted
                if (target <= nums[hi] && target > nums[mid]){
                    lo = mid + 1;
                } else {
                    hi = mid - 1;
                }
            } else {
                hi--;
            }
        }
        return false;
    }
}
```

## Solution - Binary Search (check one side)
```java
class Solution {
    public boolean search(int[] nums, int target) {
        int lo = 0, hi = nums.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (nums[mid] == target) return true;
            else if (nums[mid] > nums[lo]){ // left side is sorted
                if (target >= nums[lo] && target < nums[mid]){
                    hi = mid - 1;
                } else {
                    lo = mid + 1;
                }
            } else if (nums[mid] < nums[lo]){ // right side is sorted
                if (target <= nums[hi] && target > nums[mid]){
                    lo = mid + 1;
                } else {
                    hi = mid - 1;
                }
            } else {
                lo++;
            }
        }
        return false;
    }
}
```
### Complexity
* Time Complexity: O(n) - worst case: target: 2, nums: 11111
* Space Complexity: O(1)
