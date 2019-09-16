#  - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/number-of-segments-in-a-string/)

## Description
Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.

## Thinking & Notes
* Split: use `split()`. need to trim at first. then check `if trimmed.equals("")`. then return split using regex.
* Count the beginning of a segment: we can find and count the beginning of each segment.

## Solution - Split
```java
class Solution {
    public int countSegments(String s) {
        String trimmed = s.trim();
        if (trimmed.equals("")) {
            return 0;
        }
        return trimmed.split("\\s+").length;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

## Solution - Count the beginning of a segment
```java
class Solution {
    public int countSegments(String s) {
        int res = 0;
        for (int i = 0; i < s.length(); i++){
            if ((i==0 || s.charAt(i-1) == ' ') && s.charAt(i) != ' ')
                res++;
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(1)
* Space Complexity: O(1)
