# Reverse String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-string/description/)

Write a function that takes a string as input and returns the string reversed.

Example:

Given s = "hello", return "olleh".

## My Solution
```java
class Solution {
    public String reverseString(String s) {
        char[] str = s.toCharArray();
        int lo = 0;
        int hi = s.length() - 1;
        while (lo < hi){
            char tmp = s.charAt(lo);
            str[lo] = s.charAt(hi);
            str[hi] = tmp;
            lo++;
            hi--;
        }
        return new String(str);
    }
}
```

## Complexity
Time Complexity: O(n)