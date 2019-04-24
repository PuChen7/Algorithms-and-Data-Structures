# Sort Colors - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/sort-colors/)

## Description
Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.
Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

## Thinking & Notes
* Two Pointers: The idea is to sweep all 0s to the left and all 2s to the right, then all 1s are left in the middle.

## Solution - Two Pointers
```java
class Solution {
    public void sortColors(int[] nums) {
        int second=nums.length-1, zero=0;
        for (int i=0; i<=second; i++) {
            while (nums[i]==2 && i<second) swap(i, second--, nums);
            while (nums[i]==0 && i>zero) swap(i, zero++, nums);
        }
    }
    
    private void swap(int i, int j, int[] nums){
        int tmp = nums[j];
        nums[j] = nums[i];
        nums[i] = tmp;
    }
}
```
#### Complexity
* Time Complexity: O(2n) -> O(n)
* Space Complexity: O(1)
