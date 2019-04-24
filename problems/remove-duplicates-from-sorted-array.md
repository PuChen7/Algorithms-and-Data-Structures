# Remove Duplicates from Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

## Description
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

## Thinking & Notes
* Two Pointers: use an extra pointer to keep the next available insert point

# Solution - Two Pointers
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int index = 0;
        for (int i = 1; i < nums.length; i++){
            if (nums[i] != nums[i-1]){
                index++;
                nums[index] = nums[i];
            } 
        }
        return index+1;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
