# Valid Palindrome II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-palindrome-ii/)

## Description
Given a non-empty string s, you may delete at most one character. Judge whether you can make it a palindrome. 

## Thinking & Notes
* Two Pointers: if `isPalindrome == false`, check one more time

## Solution - Two Pointers
```java
class Solution {
    public boolean validPalindrome(String s) {
        if (s == null || s.length() == 0) return false;
        
        int left = 0, right = s.length()-1;
        while (left <= right){
            if (s.charAt(left) == s.charAt(right)){
                left++;
                right--;
            } else {
                return isPalindrome(left, right-1, s) || isPalindrome(left+1, right, s);
            }
        }
        return true;
    }
    
    private boolean isPalindrome(int i, int j, String s){
        while (i <= j){
            if (s.charAt(i) == s.charAt(j)){
                i++;
                j--;
            } else {
                return false;
            }
        }
        return true;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
