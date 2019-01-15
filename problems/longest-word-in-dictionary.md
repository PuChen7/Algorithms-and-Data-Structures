# Longest Word in Dictionary - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-word-in-dictionary/)

## Description
Given a list of strings words representing an English Dictionary, find the longest word in words that can be built one character at a time by other words in words. If there is more than one possible answer, return the longest word with the smallest lexicographical order.
If there is no answer, return the empty string.

Example 1:

Input: 
words = ["w","wo","wor","worl", "world"]

Output: "world"

Explanation: 
The word "world" can be built one character at a time by "w", "wo", "wor", and "worl".

## Thinking & Notes
* Brute Force: Use HashSet store all strings in array. for each string, check if set contains all substrings.
* Can use `Trie` to solve it.

## Solution - Brute Force
```java
class Solution {
    public String longestWord(String[] words) {
        HashSet<String> target = new HashSet<>();
        for (String w : words) target.add(w);
        String res = "";
        
        boolean isValid;
        for (String w : words){
            if (w.length() > res.length() || 
                w.length() == res.length() && w.compareTo(res) < 0){
                isValid = true;
                for (int i = 1; i < w.length(); i++){
                    if (!target.contains(w.substring(0, i))){ 
                        isValid = false;
                        break;
                    }
                }
                if (isValid) res = w;   
            }
        }
        return res;
    }
}
```
### Complexity
* Time: O(n^2)
* Space: O(n^2) for creating substrings
