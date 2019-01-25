# Arranging Coins - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/arranging-coins/)

## Description
You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.

Example 1:

n = 5

The coins can form the following rows:

¤

¤ ¤

¤ ¤

Because the 3rd row is incomplete, we return 2.

## Thinking & Notes
* General approach: check every line until remaining cannot form a line.

## Solution - General Approach
```java
class Solution {
    public int arrangeCoins(int n) {
        int res = 0;
        int count = 0;
        while (n > count){
            count++;
            n = n - (count);
            res++;
        }
        return res;
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)
