# Find Minimum in Rotated Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.

## My Solution
```java
class Solution {
    public int findMin(int[] nums) {
        if (nums.length == 1)
            return nums[0];
        int lo = 0;
        int hi = nums.length - 1;
        while (lo < hi){
            int mid = (lo+hi)/2;
            if (mid > 0 && nums[mid] < nums[mid-1])    // e.g. [6,7,1,2,3,4]
                return nums[mid];
            if (nums[mid] >= nums[lo] && nums[mid] > nums[hi])   // e.g. [4,5,6,7,1,2,3]. why nums[mid] >= nums[lo]
                lo = mid + 1;
            else
                hi = mid - 1;
        }
        return nums[lo];
    }
}
```

## Complexity
Using Binary Search.
O(logn)