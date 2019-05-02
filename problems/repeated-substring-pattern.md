# Repeated Substring Pattern - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/repeated-substring-pattern/)

## Description
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

## Thinking & Notes
* Substring
  * The length of the repeating substring must be a divisor of the length of the input string
  * Search for all possible divisor of str.length, starting for length/2
  * If i is a divisor of length, repeat the substring from 0 to i the number of times i is contained in s.length
  * If the repeated substring is equals to the input str return true


## Solution - Substring
```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        int len = s.length();
        for (int i = len/2; i >= 1; i--){
            if (len % i == 0){
                int m = len / i;    // num of total sub string
                String subS = s.substring(0,i);   // sub string
                int j;
                for (j = 1; j < m; j++){
                    if (!s.substring(i*j, i+i*j).equals(subS)) break;
                }
                if (j == m) return true;
            }
        }
        return false;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
