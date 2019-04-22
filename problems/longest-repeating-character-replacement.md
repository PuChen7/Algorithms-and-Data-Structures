# Longest Repeating Character Replacement - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-repeating-character-replacement/)

## Description
Given a string that consists of only uppercase English letters, you can replace any letter in the string with another letter 
at most k times. Find the length of a longest substring containing all repeating letters you can get after performing the 
above operations.

## Thinking & Notes
* Sliding Window: use array to keep count of letters. 

## Solution - Sliding Window
```java
class Solution {
    public int characterReplacement(String s, int k) {
        int maxCount = 0, maxLength = 0, start = 0;
        int[] count = new int[26];
        
        for (int end = 0; end < s.length(); end++){
            // maxCount -> max count of a letter
            maxCount = Math.max(maxCount, ++count[s.charAt(end)-'A']);
            // if total length exceeds, slide to right with one letter 
            if (end - start + 1 - maxCount > k) {
                count[s.charAt(start)-'A']--;
                start++;
            }
            maxLength = Math.max(maxLength, end - start + 1);
        }
        return maxLength;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
