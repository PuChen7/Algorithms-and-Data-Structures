# Palindromic Substrings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindromic-substrings/)

## Description
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

## Thinking & Notes
* Extend even and odd: for each character, try to extend palindrome substring.

## Solution - Extend even and odd
```java
class Solution {
    int count = 0;
    public int countSubstrings(String s) {
        if (s == null || s.length() == 0) return 0;
        
        for (int i = 0; i < s.length(); i++){
            helper(i, i, s);
            helper(i, i+1, s);
        }
        return count;
    }
    
    private void helper(int left, int right, String s){
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)){
            count++; left--; right++;
        }
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)
