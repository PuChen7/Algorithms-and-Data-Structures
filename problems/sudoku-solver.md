# Sudoku Solver - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/sudoku-solver/description/)

Write a program to solve a Sudoku puzzle by filling the empty cells.

Empty cells are indicated by the character '.'.

You may assume that there will be only one unique solution.

## My Solution
```java
class Solution {
    public void solveSudoku(char[][] board) {
        if (board == null || board.length == 0){
            return;
        }
        solve(board);
    }
    
    private boolean solve(char[][] board){
        for (int i = 0; i < board.length; i++){     // traverse row
            for (int j = 0; j < board[0].length; j++){  // traverse column
                if (board[i][j] == '.'){    // find a empty spot
                    for (char num = '1'; num <= '9'; num++){    // try number through 1 to 9
                        if (isValid(board, i, j, num)){ // if this spot is valid
                            board[i][j] = num;  // store this number into the spot 
                            if (solve(board)){  // go deeper
                                return true;
                            }else{
                                board[i][j] = '.';  // if not valid, set the spot to empty
                            }
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }
    
    private boolean isValid(char[][] board, int row, int col, char c){
        for(int i = 0; i < 9; i++) {
            if(board[i][col] != '.' && board[i][col] == c) return false; //check row
            if(board[row][i] != '.' && board[row][i] == c) return false; //check column
            if(board[3 * (row / 3) + i / 3][ 3 * (col / 3) + i % 3] != '.' && 
                board[3 * (row / 3) + i / 3][3 * (col / 3) + i % 3] == c) return false; //check 3*3 block
        }
        return true;
    }
}
```

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Combination Sum III](combination-sum3.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)

* [Combination](combination.md)

* [Generate Parentheses](generate-parentheses.md)