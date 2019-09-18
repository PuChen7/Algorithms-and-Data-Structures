# Binary String With Substrings Representing 1 To N - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-string-with-substrings-representing-1-to-n/)

## Description
Given a binary string S (a string consisting only of '0' and '1's) and a positive integer N, return true if and only if for every integer X from 1 to N, the binary representation of X is a substring of S.

## Thinking & Notes
* Check all numbers: for each 1 to N, check if satisfy

## Solution - Check all numbers
```java
class Solution {
    public boolean queryString(String S, int N) {
        for (int i = 1; i <= N; i++){
            if (!S.contains(Integer.toBinaryString(i))) return false;
        }
        return true;
    }
}
```
#### Complexity
* Time Complexity: O(N * complexity of contains())
* Space Complexity: O(1)
