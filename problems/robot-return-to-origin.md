# Robot Return to Origin - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/robot-return-to-origin/)

## Description
There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot ends up at (0, 0) after it completes its moves.

The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

## Thinking & Notes
* O(n): to return to (0,0), the count of `U` should equal to `D`. same for `L` and `R`.

## Solution - O(n)
```java
class Solution {
    public boolean judgeCircle(String moves) {
        int x = 0;
        int y = 0;
        for (char ch : moves.toCharArray()) {
            if (ch == 'U') y++;
            else if (ch == 'D') y--;
            else if (ch == 'R') x++;
            else if (ch == 'L') x--;
        }
        return x == 0 && y == 0;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
