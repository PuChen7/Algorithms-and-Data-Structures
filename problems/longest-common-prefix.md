# Longest Common Prefix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-common-prefix/)

## Description
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

## Thinking & Notes
* Horizontal scan: for each string, reduce until found. 
  * The key idea is the longest common prefix is valid for all strings, so we can take any one and check if it's longest common prefix for all other strings, if not, reduce one char at the end, then check again until we found.
* Vertical scan: check char one by one

## Solution - Horizontal scan 
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

## Solution - Vertical scan 
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        // vertical scanning
        // check char by char
        if (strs == null || strs.length == 0) return "";
        for (int i = 0; i < strs[0].length(); i++){
            char c = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j++){
                if (i == strs[j].length() || c != strs[j].charAt(i))
                    return strs[j].substring(0, i);
            }
        }
        return strs[0];
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
