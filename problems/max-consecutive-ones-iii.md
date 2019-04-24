# Max Consecutive Ones III - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/max-consecutive-ones-iii/)

## Description
Given an array A of 0s and 1s, we may change up to K values from 0 to 1.

Return the length of the longest (contiguous) subarray that contains only 1s. 

## Thinking & Notes
* Sliding Window: similar to [Longest Repeating Character Replacement](problems/longest-repeating-character-replacement.md).

## Solution - Sliding Window
```java
class Solution {
    public int longestOnes(int[] A, int K) {
        int start = 0, end;
        for (end = 0; end < A.length; end++){
            if (A[end] == 0) K--;
            if (K < 0 && A[start++] == 0) K++;
        }
        return end - start;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

