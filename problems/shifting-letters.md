# Shifting Letters - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/shifting-letters/)

## Description
We have a string S of lowercase letters, and an integer array shifts.

Call the shift of a letter, the next letter in the alphabet, (wrapping around so that 'z' becomes 'a'). 

For example, shift('a') = 'b', shift('t') = 'u', and shift('z') = 'a'.

Now for each shifts[i] = x, we want to shift the first i+1 letters of S, x times.

Return the final string after all such shifts to S are applied.

## Thinking & Notes
* Prefix Sum: first number shift `shift[n]` times, second shift `shift[n-1]` times ... last shift `one` time

## Solution - Prefix Sum
```java
class Solution {
    public String shiftingLetters(String S, int[] shifts) {
        StringBuilder sb = new StringBuilder(S);
        for (int i = S.length() - 2; i >= 0; i--)
            shifts[i] = (shifts[i] + shifts[i+1]) % 26; // mod 26 to prevent overflow
        for (int i = 0; i < S.length(); i++)
            sb.setCharAt(i, (char)((S.charAt(i) - 'a' + shifts[i]) % 26 + 'a'));
        return sb.toString();
    }
}
```
#### Complexity
* Time Complexity: O(N)
* Space Complexity: O(N)

### Core Algorithm & Data Sructure
* Prefix Sum
