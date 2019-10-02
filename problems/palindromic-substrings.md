# Palindromic Substrings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindromic-substrings/)

## Description
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

## Thinking & Notes
* Brute Force (`Time Limit Exceeded!`): Although this approach is not accepted by leetcode, this could be a good choice in the interview because it's straightforward. Get all substrings of a string, then check every substring if it is a palindrome.
* Extend even and odd: for each character, try to extend palindrome substring.
* Dynamic Programming: the key idea for dp approach is to memorize and reuse subproblem's answer.

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

## Solution - Dynamic Programming
```java
 /**
    Hint: Using dp matrix to look up whether the previous closure equals or not
    
    For instance, acdca
    1. a (x-axis) -> a (Y-axis) = true
      a c d c a
    a T
    c 
    d     
    c       
    a
    
    2. c->c = T, a->c = F
      a c d c a
    a T
    c F T
    d     
    c       
    a
    
    3. d->d=T, c->d=F, a->d=F
      a c d c a
    a T
    c F T
    d F F T   
    c       
    a
    
    4. c->c=T, d->c=F, c->c=T (look up the previous closure d->d)=T, c->a=F
      a c d c a
    a T
    c F T
    d F F T   
    c F T F T
    a
    
    5. a->a=T, c->a=F, d->a=F, c->a=F, a->a=T(look up the previous previous c->c=T(includes its previous closure(d->d))
      a c d c a
    a T
    c F T
    d F F T   
    c F T F T
    a T F F F T
    
    Count all the T, we get 7
    Time complexity, N+N-1+N-2+....+1 = O(N(1+N)/2) = O(N^2)
    
    */
class Solution {
    public int countSubstrings(String s) {
        int res = 0;
        boolean[][] dp = new boolean[s.length()][s.length()];
        for (int i = 0; i < s.length(); i++){
            for (int j = i; j >=0; j--){
                if (s.charAt(i) == s.charAt(j)){
                    // why i - j < 3? consider AXA, i-j == 2, no matter what X is, this is palindrome
                    // why dp[i-1][j+1] == true? consider abcba, when we checking if this is palindeome
                        // we can check if bcb is palindrome, because bcb is already checked before. This is DP! 
                    if (i - j < 3 || dp[i-1][j+1] == true){
                        res++;
                        dp[i][j] = true;
                    }
                }
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n^2)

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
