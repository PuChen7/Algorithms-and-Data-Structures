# Generate Parentheses - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/generate-parentheses/description/)

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]

## My Solution
```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList();
        backtrack(list, "", 0, 0, n);
        return list;
    }
    
    private void backtrack(List<String> list, String str, int open, int close, int n){
        if (str.length() == n*2){
            list.add(str);
            return;
        }
        if (open < n){
            backtrack(list, str+"(", open+1, close, n);
        }
        if (close < open){
            backtrack(list, str+")", open, close+1, n);
        }
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

* [Sudoku Solver](sudoku-solver.md)