# Longest Common Subsequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-common-subsequence/)

## Description
Given two strings text1 and text2, return the length of their longest common subsequence.

A subsequence of a string is a new string generated from the original string with some characters(can be none) deleted without changing the relative order of the remaining characters. (eg, "ace" is a subsequence of "abcde" while "aec" is not). A common subsequence of two strings is a subsequence that is common to both strings.

## Thinking & Notes
* Brute force:
  - try all combinations, if char not match, go further 2 options, each string move one char.
  - this approach is used in [Delete Operation for Two Strings](delete-operation-for-two-strings.md)
* Recursive DP with Mem
  - same idea with [Delete Operation for Two Strings](delete-operation-for-two-strings.md)
  - use 2-d array to store visited pair
* Non-Recursive DP: same idea

## Solution - Brute force - Time Limit Exceeded
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        return helper(text1, text2, 0, 0, 0);
    }
    
    private int helper(String s1, String s2, int count, int i, int j){
        if (i == s1.length() || j == s2.length()) return count;
        if (s1.charAt(i) == s2.charAt(j)) return helper(s1, s2, count+1, i+1, j+1);
        return Math.max(helper(s1, s2, count, i+1, j), helper(s1, s2, count, i, j+1));
    }
}
```
#### Complexity
* Time Complexity: O(3^(m+n))
* Space Complexity: O(1)

## Solution - Recursive DP with Mem
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int[][] mem = new int[text1.length()+1][text2.length()+1];
        return helper(text1, text2, mem, 0, 0);
    }
    
    private int helper(String s1, String s2, int[][] mem, int i, int j){
        if (i == s1.length() || j == s2.length()) return 0;
        if (s1.charAt(i) == s2.charAt(j)) mem[i][j] = helper(s1, s2, mem, i+1, j+1) + 1;
        if (mem[i][j] > 0) return mem[i][j];
        mem[i][j] = Math.max(helper(s1, s2, mem, i+1, j), helper(s1, s2, mem, i, j+1));
        return mem[i][j];
    }
}
```
#### Complexity
* Time Complexity: O(m*n)
* Space Complexity: O(m*n)

## Solution - Non-Recursive DP with Mem
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int[][] mem = new int[text1.length()+1][text2.length()+1];
        for (int i = 0; i < text1.length(); i++){
            for (int j = 0; j < text2.length(); j++){
                if (text1.charAt(i) == text2.charAt(j)) mem[i+1][j+1] = 1 + mem[i][j];
                else mem[i+1][j+1] = Math.max(mem[i][j+1], mem[i+1][j]);
            }
        }
        return mem[text1.length()][text2.length()]; 
    }
}
```
#### Complexity
* Time Complexity: O(m*n)
* Space Complexity: O(m*n)
