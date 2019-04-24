# Remove Duplicates from Sorted Array II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

## Description
Given a sorted array nums, remove the duplicates in-place such that duplicates appeared at most twice and return the new length.

## Thinking & Notes
* Two Pointers: The two pointers i and n start at the same time and point to a position. When the current value does not need to be larger than the previous one, it means that 3 are present.
Or more than 3 identical values, at this time the if condition is not satisfied, i stays in the unsatisfied position, waiting for the next larger number to be replaced, when the next larger one appears
The number again satisfies the if condition, replacing the position pointed to by i with the number, i pointing to the next waiting for replacement, and the if condition is again used to detect the replacement.
The number is guaranteed to not appear more than two repetitions.

## Solution - Two Pointers
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int i = 0;
        for (int n : nums){
            if (i < 2 || n > nums[i-2])
                nums[i++] = n;
        }
        return i;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

### More About this Algorithm & Data Structure?
This problem can be modified to  `at most K duplicates`
```java
int removeDuplicates(vector<int>& nums, int k) {
    int i = 0;
    for (int n : nums)
        if (i < k || n > nums[i-k])
            nums[i++] = n;
    return i;
}
```
