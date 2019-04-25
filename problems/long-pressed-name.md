# Long Pressed Name - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/long-pressed-name/)

## Description
Your friend is typing his name into a keyboard.  Sometimes, when typing a character c, the key might get long pressed, and the character will be typed 1 or more times.

You examine the typed characters of the keyboard.  Return True if it is possible that it was your friends name, with some characters (possibly none) being long pressed.

## Thinking & Notes
* Two Pointers: iterate through the `typed` string, check `name` at the same time. 

## Solution - Two Pointers
```java
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        int j = 0;
        for (int i = 0; i < typed.length(); i++){
            if (name.charAt(j) == typed.charAt(i)) j++;
            if (j == name.length()) return true;
        }
        return false;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
