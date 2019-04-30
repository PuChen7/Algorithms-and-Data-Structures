# Reverse String II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-string-ii/)

## Description
Given a string and an integer k, you need to reverse the first k characters for every 2k characters counting from the start of the string. If there are less than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and left the other as original. 

## Thinking & Notes
* Direct: iterate string char by char. 

## Solution - Direct
```java
class Solution {
    public String reverseStr(String s, int k) {
        char[] strArr = s.toCharArray();
        for (int i = 0; i < strArr.length; i += 2*k){
            int start = i, end = Math.min(i+k-1, strArr.length-1);
            while (start < end){
                char tmp = strArr[start];
                strArr[start++] = strArr[end];
                strArr[end--] = tmp;
            }
        }
        return new String(strArr);
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
