# Smallest Subsequence of Distinct Characters - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/)

## Description
Return the lexicographically smallest subsequence of text that contains all the distinct characters of text exactly once.

## Thinking & Notes
* Stack: the key idea is for example: `cdadabc`, we push `cd` in stack, now pushing `a`, we see `a` is smaller than `d` in lex order,
and there's `d` after `a`, then we should pop current `d` in stack, and later push `d` after `a`. 
  - Find the index of last occurrence for each character.
  - Use a stack to keep the characters for result.
  - Loop on each character in the input string S,
  - if the current character is smaller than the last character in the stack,
  - and the last character exists in the following stream,
  - we can pop the last character to get a smaller result.


## Solution - Stack
```java
class Solution {
    public String smallestSubsequence(String text) {
        boolean[] seen = new boolean[26];
        int[] last = new int[26];
        Stack<Integer> stack = new Stack<>();
        
        for (int i = 0; i < text.length(); i++)
            last[text.charAt(i) - 'a'] = i;
        
        for (int i = 0; i < text.length(); i++){
            int c = text.charAt(i) - 'a';
            if (seen[c]) continue;
            while (!stack.isEmpty() && stack.peek() > c && last[stack.peek()] > i){
                seen[stack.pop()] = false;
            } 
            stack.push(c);
            seen[c] = true;
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i : stack) sb.append((char) (i + 'a'));
        return sb.toString();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

### Core Algorithm & Data Sructure
- Stack

