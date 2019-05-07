# Length of Last Word - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/length-of-last-word/)

## Description
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

## Thinking & Notes
* Iterate from tail: return difference when `s.charAt(i) == ' '`

## Solution - Iterate from tail
```java
class Solution {
    public int lengthOfLastWord(String s) {
        s = s.trim();
        for (int i = s.length()-1; i >= 0; i--){
            if (s.charAt(i) == ' ') return s.length() - i - 1;
        }
        return s.length();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
