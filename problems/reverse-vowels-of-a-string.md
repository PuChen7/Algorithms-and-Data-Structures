# Reverse Vowels of a String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-vowels-of-a-string/)

## Description
Write a function that takes a string as input and reverse only the vowels of a string.

## Thinking & Notes
* Two Pointers: head and tail move towards center. 

## Solution - Two Pointers
```java
class Solution {
    public String reverseVowels(String s) {
        if(s == null || s.length()==0) return s;
        String vowels = "aeiouAEIOU";
        char[] chars = s.toCharArray();
        int start = 0;
        int end = s.length()-1;
        while(start<end){
            while(start<end && !vowels.contains(chars[start]+""))
                start++;

            while(start<end && !vowels.contains(chars[end]+""))
                end--;

            char temp = chars[start];
            chars[start] = chars[end];
            chars[end] = temp;

            start++;
            end--;
        }
        return new String(chars);
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

