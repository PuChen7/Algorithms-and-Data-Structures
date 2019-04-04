# Find Peak Element - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-peak-element/)

## Description
A peak element is an element that is greater than its neighbors.

Given an input array nums, where nums[i] ≠ nums[i+1], find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that nums[-1] = nums[n] = -∞.

## Thinking & Notes
* Brute force: iterate array and check if `nums[i] > nums[i-1] && nums[i] > nums[i+1]`.
* Optimized brute force: no need to check both sides. keep checking the next value.
* Iterative Binary Search:
  * `mid` lies in `descending` sequence of numbers: `peak` must at left of `mid`
  * `mid` lies in `ascending` sequence of numbers: `peak` must at right of `mid`

## Solution - Brute force
```java
class Solution {
    public int findPeakElement(int[] nums) {
        if (nums.length == 1) return 0;
        for (int i = 0; i < nums.length; i++){
            if (i == 0){
                if (nums[i] > nums[i+1]) return i;
            } else if (i == nums.length-1){
                if (nums[i] > nums[i-1]) return i;
            } else {
                if (nums[i] > nums[i+1] && nums[i] > nums[i-1])
                    return i;
            }
        } 
        return 0;
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Brute force
```java
class Solution {
    public int findPeakElement(int[] nums) {
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] > nums[i + 1])
                return i;
        }
        return nums.length - 1;
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Iterative Binary Search
```java
class Solution {
    public int findPeakElement(int[] nums) {
        int lo = 0, hi = nums.length-1;
        while (lo < hi) {
            int mid = lo + (hi - lo) / 2;
            if (nums[mid] > nums[mid+1])
                hi = mid;
            else
                lo = mid + 1;
        }
        return lo;
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)
