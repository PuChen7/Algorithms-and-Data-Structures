# Longest Palindromic Substring - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-palindromic-substring/)

## Description
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:

Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.

## Thinking & Notes
- Brute Force: pick all possible starting and ending positions for a substring, and verify if it is a palindrome.
  - Time complexity : O(n^3)
- [Longest common substring problem](https://www.geeksforgeeks.org/longest-common-substring-dp-29/):  
each time we find a longest common substring candidate, 
we check if the substring’s indices are the same as the reversed substring’s original indices. 
If it is, then we attempt to update the longest palindrome found so far; 
if not, we skip this and find the next candidate.
- Dynamic Programming:  
- Expand Around Center: expand from center, there are two kinds of centers, (a, aa). 

## Solution - Expand Around Center
```java
class Solution {
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";
        int start = 0, end = 0;
        for (int i = 0; i < s.length(); i++){
            int len1 = expandCenter(s, i, i);
            int len2 = expandCenter(s, i, i+1);
            int len = Math.max(len1, len2);
            if (len > end - start){
                start = i - (len - 1)/2;
                end = i + len/2;
            }
        }
        return s.substring(start, end+1);
    }
    
    private int expandCenter(String s, int l, int r){
        while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)){
            l--;
            r++;
        }
        return r - l - 1;
    }
}
```
### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)
