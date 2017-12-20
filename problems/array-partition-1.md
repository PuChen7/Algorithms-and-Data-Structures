# Array Partition I - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/array-partition-i/description/)

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ...,
(an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

```java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int result = 0;
        for (int i = 0; i < nums.length; i += 2){
            result += nums[i];
        }
        return result;
    }
}
```
Suppose there's an array with entries: [1, 2, 3, 4, 5, 6] (after sorted),
then the largest min(a1, b1) will be [1, 3, 5].
