# Rotate Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/rotate-array/description/)

Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

## My Solution - Version I
```java
class Solution {
    public void rotate(int[] nums, int k) {
        k = k % nums.length;    // prevent invlid input such as: [1] 2
        reverse(nums, 0, nums.length-1);
        reverse(nums, 0, k-1);
        reverse(nums, k, nums.length-1);
    }
    
    public void reverse(int[] nums, int start, int end){
        while (start < end){
            int tmp = nums[start];
            nums[start] = nums[end];
            nums[end] = tmp;
            start++;
            end--;
        }
    }
}
```