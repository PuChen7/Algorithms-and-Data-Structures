# Remove Element - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/remove-element/)

## Description
Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

## Thinking & Notes
* Two pointers: because order doesn't matter, move all elements which `element != val` to position of the extra pointer.
## Solution - Two Pointers
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int j = 0;
        for (int i = 0; i < nums.length; i++){
            if (nums[i] != val)
                nums[j++] = nums[i];
        }
        return j;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
