# Valid Palindrome - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-palindrome/)

## Description
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

## Thinking & Notes
* Two Pointers: head and tail, move towards center

## Solution - Two Pointers
```java
class Solution {
    public boolean isPalindrome(String s) {
        if (s.length() == 0) return true;
        int left = 0, right = s.length()-1;
        while (left < right) {
            if (!Character.isLetterOrDigit(s.charAt(left))){
                left++;
            } else if (!Character.isLetterOrDigit(s.charAt(right))){
                right--;
            } else {
                if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) return false;
                left++;
                right--;
            }
        }
        return true;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
