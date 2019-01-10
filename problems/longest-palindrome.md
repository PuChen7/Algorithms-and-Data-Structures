# Longest Palindrome - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-palindrome/submissions/)

## Description
Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

Note:
Assume the length of given string will not exceed 1,010.

Example:

Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.

## Thinking & Notes
* What is special about `palindrome`?
  * pairs of letter, can contain one extra single letter
* Using set: do it pair by pair. store one item, if next loop cannot add this item, it indicates a duplicate. duplicate means a pair, then remove the item from the set and increment result.

## My Solution
```java
class Solution {
    public int longestPalindrome(String s) {
        if (s == null) return 0;
        HashSet<Character> set = new HashSet<Character>();
        int res = 0;
        
        for (int i = 0; i < s.length(); i++){
            if (set.contains(s.charAt(i))){
                set.remove(s.charAt(i));
                res += 1;
            } else {
                set.add(s.charAt(i));
            }
        }
        if (!set.isEmpty()) return res*2 + 1;
        return res*2;
    }
}
```
