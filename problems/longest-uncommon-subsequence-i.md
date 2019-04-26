# Longest Uncommon Subsequence I - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-uncommon-subsequence-i/)

## Description
Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings. 

## Thinking & Notes
* Simple

## Solution - Simple
```java
class Solution {
    public int findLUSlength(String a, String b) {
        if (a.equals(b))
            return -1;
        else return Math.max(a.length(), b.length());
    }
}
```
#### Complexity
* Time Complexity: O(1)
* Space Complexity: O(1)
