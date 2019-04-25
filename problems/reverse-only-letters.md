# everse Only Letters - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-only-letters/)

## Description
Given a string S, return the "reversed" string where all characters that are not a letter stay in the same place, and all letters reverse their positions.

## Thinking & Notes
* Two Pointers: two pointers move toward center
* Stack: first-in-last-out

## Solution - Two Pointers
```java
class Solution {
    public String reverseOnlyLetters(String S) {
        StringBuilder sb = new StringBuilder();
        int j = S.length() - 1;
        for (int i = 0; i < S.length(); i++){
            if (Character.isLetter(S.charAt(i))){
                while (!Character.isLetter(S.charAt(j))) j--;
                sb.append(S.charAt(j--));
            } else {
                sb.append(S.charAt(i));
            }
        }
        return sb.toString();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Stack
```java
class Solution {
    public String reverseOnlyLetters(String S) {
        Stack<Character> letters = new Stack();
        for (char c: S.toCharArray())
            if (Character.isLetter(c))
                letters.push(c);

        StringBuilder ans = new StringBuilder();
        for (char c: S.toCharArray()) {
            if (Character.isLetter(c))
                ans.append(letters.pop());
            else
                ans.append(c);
        }

        return ans.toString();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
