# Swap For Longest Repeated Character Substring - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/swap-for-longest-repeated-character-substring/)

## Description
Given a string text, we are allowed to swap two of the characters in the string. Find the length of the longest substring with repeated characters.

## Thinking & Notes
* General: 
  - need an array to count occurrences of each letter
  - need to create a class to hold each longest repeating char with start and end indexes
  - two scenarios:
    - aaabba: find another `a` to replace `b` to increase maxlen+1; so result would be aaaabb.
    - aabaaba: firstly find the middle char b, length equals to 1, then make sure the left side and right side character are the same, then find if there is another a to replace b, update maxLen accordingly.

## Solution - General
```java
class Solution {
    public int maxRepOpt1(String text) {
        List<RepeatingPart> list = new ArrayList<>();
        int start = 0, end = 0;
        int[] countChar = new int[26];
        char c = text.charAt(0);
        countChar[c - 'a']++; 
        int i = 1;
        
        while (i < text.length()){
            char curr = text.charAt(i);
            countChar[curr - 'a']++;
            if (c != curr){
                list.add(new RepeatingPart(c, start, end));
                c = curr;
                start  = i;
                end = i;
            } else {
                end = i;
            }
            i++;
        }
        list.add(new RepeatingPart(c, start, end)); // add last part, because it's not added yet after loop
        
        int maxLen = 1, currLen = 0;
        // first case
        for (int j = 0; j < list.size(); j++){
            RepeatingPart rp = list.get(j);
            currLen = rp.end - rp.start + 1;
            if (currLen < countChar[rp.c - 'a']) currLen++;
            maxLen = Math.max(maxLen, currLen);
        }
        
        // secound case
        for (int j = 1; j < list.size()-1; j++){
            RepeatingPart before = list.get(j-1);
            RepeatingPart mid = list.get(j);
            RepeatingPart after = list.get(j+1);
            
            int beforeLen = before.end - before.start + 1;
            int afterLen = after.end - after.start + 1;
            
            if (mid.start == mid.end && before.c == after.c){
                currLen = beforeLen + afterLen;
                if (currLen < countChar[before.c - 'a']) currLen++;
            }
            maxLen = Math.max(maxLen, currLen);
        }
        
        return maxLen;
    }
    
    class RepeatingPart{
        char c;
        int start;
        int end;
        public RepeatingPart(char c, int start, int end){
            this.c = c;
            this.start = start;
            this.end = end;
        }
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
