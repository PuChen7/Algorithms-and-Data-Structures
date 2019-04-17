# Is Subsequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/is-subsequence/)

## Description
 Given a string s and a string t, check if s is subsequence of t.

You may assume that there is only lower case English letters in both s and t. t is potentially a very long (length ~= 500,000) string, and s is a short string (<=100). 

## Thinking & Notes
* Traverse: check every character

## Solution - Traverse
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        if (s.length() == 0) return true;
        int i = 0, j = 0;
        while (j < t.length()){
            if (t.charAt(j) == s.charAt(i)){
                i++;
                if (i == s.length()) return true;
            }
            j++;
        }
        return false;
    }
}
```
#### Complexity
* Time Complexity: O(nm)
* Space Complexity: O(1)
