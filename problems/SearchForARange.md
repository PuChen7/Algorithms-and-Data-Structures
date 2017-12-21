# Search For A Range - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-for-a-range/description/)

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].

```java
class Solution {
    private int binarySearch(boolean isLeft, int[] nums, int target){
        int lo = 0;
        int hi = nums.length;
        
        while (lo < hi){
            int mid = (lo + hi)/2;
            if (nums[mid] > target || (nums[mid] == target && isLeft == true)){
                hi = mid;
            } else {
                lo = mid + 1;
            }
        }
        return lo;
    }
    
    public int[] searchRange(int[] nums, int target) {
        int[] result = {-1, -1};
        
        int index0 = binarySearch(true, nums, target);
        
        if (index0 == nums.length || nums[index0] != target){
            return result;
        }
        
        result[0] = index0;
        result[1] = binarySearch(false, nums, target)-1;
        return result;
    }
}
```

