# Missing Number - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/missing-number/description/)

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

## My Solution - Version I
```java
class Solution {
    public int missingNumber(int[] nums) {
        int sum = (nums.length*(nums.length+1))/2;
        for (int i = 0; i < nums.length; i++)
            sum -= nums[i];
        return sum;
    }
}
```

Time Complexity: O(n)
