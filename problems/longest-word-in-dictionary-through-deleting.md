# Longest Word in Dictionary through Deleting - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-word-in-dictionary-through-deleting/)

## Description
Given a string and a string dictionary, find the longest string in the dictionary that can be formed by deleting some characters of the given string. If there are more than one possible results, return the longest word with the smallest lexicographical order. If there is no possible result, return the empty string. 

## Thinking & Notes
* Two Pointers: Compare each word with current result while iterating the dictionary.

## Solution - Two Pointers
```java
class Solution {
    public String findLongestWord(String s, List<String> d) {
        String res = "";
        for (String w : d){
            if (w.length() < res.length()) continue; // eliminate word that length is less then current res
            int j = 0; 
            for (int i = 0; i < s.length(); i++){ // iterate s and compare with word
                if (s.charAt(i) == w.charAt(j)) j++; // increment word index, compare with next char
                if (j == w.length()){ // if reached word length, it means s contains this word
					// check length and lexicographical order 
                    if (w.length() > res.length() || 
                        (w.length() == res.length() && w.compareTo(res) < 0)) res = w;
                    break;
                }
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(N*S), N is the length of dictionary, S is the length of String s.
* Space Complexity: O(1)
