# Subarray Product Less Than K - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/subarray-product-less-than-k/)

## Description
Your are given an array of positive integers nums.

Count and print the number of (contiguous) subarrays where the product of all the elements in the subarray is less than k.

## Thinking & Notes
* Sliding Window: classic sliding window. 

## Solution - Sliding Window
```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        if (k <= 1) return 0;
        int left = 0, sum = 1, res = 0;
        for (int right = 0; right < nums.length; right++){
            sum = sum * nums[right];
            while (sum >= k) sum /= nums[left++];
            res += right - left + 1;
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
