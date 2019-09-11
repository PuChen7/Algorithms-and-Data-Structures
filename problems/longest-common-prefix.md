# Longest Common Prefix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-common-prefix/)

## Description
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

## Thinking & Notes
* indexOf: for each string, reduce until found. Horizontal scan.

## Solution - indexOf 
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";
        String str = strs[0];
        int i = 0;
        for (String s : strs){
            while (s.indexOf(str) != 0)
                str = str.substring(0,str.length()-1);
        }
        return str;
    }
}
```
#### Complexity
* Time Complexity: O(n) - n is total length of all strings.
* Space Complexity: O(1)
