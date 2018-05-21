# Reverse Words in a String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-words-in-a-string/description/)

Given an input string, reverse the string word by word.

Example:  

Input: "the sky is blue",

Output: "blue is sky the".

## Solution 
```java
public class Solution {
    public String reverseWords(String s) {
        if (s == null) return null;
        
        char[] arr = s.toCharArray();
        int n = arr.length;
        
        reverse(arr, 0, n-1);
        reverseWord(arr, n);
        return clean(arr, n);
    }
    
    // method for reverse entire string
    public void reverse(char[] arr, int lo, int hi){
        while (lo < hi){
            char tmp = arr[lo];
            arr[lo] = arr[hi];
            arr[hi] = tmp;
            lo++;
            hi--;
        }
    }
    
    // method for cleaning spaces
    public String clean(char[] arr, int n){
        int i = 0, j = 0;
        // move all valid chars to front
        while (j < n){
            while (j < n && arr[j] == ' ') j++; // skip leading spaces
            while (j < n && arr[j] != ' ') arr[i++] = arr[j++]; // skip non space
            while (j < n && arr[j] == ' ') j++; // skip trailing spaces
            if (j < n) arr[i++] = ' ';  // set space
        }
        return new String(arr).substring(0, i);
    }
    
    // method for reverse single word
    public void reverseWord(char[] arr, int n){
        int lo = 0, hi = 0;
        while (lo < n){
            while (lo < hi || lo < n && arr[lo] == ' ') lo++;
            while (hi < lo || hi < n && arr[hi] != ' ') hi++;
            reverse(arr, lo, hi-1);
        }
    }
}
```