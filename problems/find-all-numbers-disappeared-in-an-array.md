# Largest Number At Least Twice of Others - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/largest-number-at-least-twice-of-others/description/)

In a given integer array nums, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the index of the largest element, otherwise return -1.

## My Solution - Version I
```java
class Solution {
    public int dominantIndex(int[] nums) {
        if (nums == null || nums.length < 2) return 0;
        
        int largest = nums[0];
        for (int i = 1; i < nums.length; i++)
            if (nums[i] > largest) largest = nums[i];
        int index = 0;
        for (int i = 0; i < nums.length; i++){
            if (nums[i] == largest) {
                index = i;
                continue;
            }
            if (largest < nums[i]*2) return -1;
        }
        return index;
    }
}
```

Time Complexity: O(n)