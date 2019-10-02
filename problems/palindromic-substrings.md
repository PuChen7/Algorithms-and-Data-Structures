# Palindromic Substrings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindromic-substrings/)

## Description
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

## Thinking & Notes
* Brute Force (`Time Limit Exceeded!`): Although this approach is not accepted by leetcode, this could be a good choice in the interview because it's straightforward. Get all substrings of a string, then check every substring if it is a palindrome.
* Extend even and odd: for each character, try to extend palindrome substring.

## Solution - Brute Force - `Time Limit Exceeded`
```java
class Solution {
    public int countSubstrings(String s) {
        int count = 0;
        List<String> sub = subString(s);
        for (String str : sub) if (isPalindrome(str)) count++;
        return count;
    }
    
    public List<String> subString(String s) {
        List<String> sub = new ArrayList<>();
        for (int i = 0; i < s.length(); i++){
           for (int j = i+1; j <= s.length(); j++){
                sub.add(s.substring(i, j));
            } 
        }
        return sub;
    } 
    
    public boolean isPalindrome(String s) {
        // reverse the given String 
        String reverse = new StringBuffer(s).reverse().toString(); 
        // check whether the string is palindrome or not 
        if (s.equals(reverse)) return true;
        else return false;
    } 
}
```
#### Complexity
* Time Complexity: O(n^2 + n) ?
* Space Complexity: O(n) ?

## Solution - Extend even and odd
```java
class Solution {
    int count = 0;
    public int countSubstrings(String s) {
        if (s == null || s.length() == 0) return 0;
        
        for (int i = 0; i < s.length(); i++){
            helper(i, i, s);
            helper(i, i+1, s);
        }
        return count;
    }
    
    private void helper(int left, int right, String s){
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)){
            count++; left--; right++;
        }
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)
