# Max Consecutive Ones - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/max-consecutive-ones/description/)

Given a binary array, find the maximum number of consecutive 1s in this array.

Example 1:

Input: [1,1,0,1,1,1]

Output: 3

Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.

## My Solution
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int res = 0;
        for (int i = 0; i < nums.length; i++){
            if (nums[i] == 1){
                count += 1;
                if (count > res) res = count;
            }
            else count = 0;
        }
        return res;
    }
}
```

## Complexity
Time Complexity: O(n)