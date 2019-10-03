# Alphabet Board Path - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/alphabet-board-path/)

## Description
On an alphabet board, we start at position (0, 0), corresponding to character board[0][0].

Here, board = ["abcde", "fghij", "klmno", "pqrst", "uvwxy", "z"], as shown in the diagram below.
Return a sequence of moves that makes our answer equal to target in the minimum number of moves.  You may return any path that does so.

## Thinking & Notes
* Move: the key is how to calculate position of target. and also move `Up` and `Right` first, in this way we can prevent some corner cases like `Z`.

## Solution - Move
```java
class Solution {
    public String alphabetBoardPath(String target) {
        if (target == "") return "";
        StringBuilder sb = new StringBuilder();
        int currRow = 0, currCol = 0;
        char[] tar = target.toCharArray();
        for (int i = 0; i < tar.length; i++){
            int tarRow = (tar[i] - 'a') / 5;
            int tarCol = (tar[i] - 'a') % 5;
            if (currRow == tarRow && currCol == tarCol) sb.append("!");
            else{
                appendPath(tarRow, tarCol, sb, currRow, currCol);
                sb.append("!");
                currRow = tarRow;
                currCol = tarCol;
            }
        }
        return sb.toString();
    }
    
    private void appendPath(int tarRow, int tarCol, StringBuilder sb, int currRow, int currCol){
        while (currRow > tarRow){
            sb.append("U");
            currRow--;
        }
        while (currCol < tarCol){
            sb.append("R");
            currCol++;
        }
        while (currCol > tarCol){
            sb.append("L");
            currCol--;
        }
        while (currRow < tarRow){
            sb.append("D");
            currRow++;
        }
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(m)
