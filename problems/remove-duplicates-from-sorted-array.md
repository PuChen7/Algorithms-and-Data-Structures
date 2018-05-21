# Remove Duplicates from Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

# Solution
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length < 2) return nums.length;
        
        int len = 1;
        for (int i = 1; i < nums.length; i++)
            if (nums[i] != nums[i-1]) nums[len++] = nums[i];
        
        return len;
    }
}
```
## Complexity
Time Complexity: O(n)