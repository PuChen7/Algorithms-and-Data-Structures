# Product of Array Except Self - from [LeetCode](https://leetcode.com)
View this problem on LeetCode](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/)

```java 
public class Solution {
public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] result = new int[n];
    result[0] = 1;
    for (int i = 1; i < n; i++) {
        result[i] = result[i - 1] * nums[i - 1];
    }
    int right = 1;
    for (int i = n - 1; i >= 0; i--) {
        result[i] *= right;
        right *= nums[i];
    }
    return result;
}
```
