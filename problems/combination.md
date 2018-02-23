# Combination - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/combinations/description/)

Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

For example,
If n = 4 and k = 2, a solution is:

[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]

## My Solution
```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> list = new ArrayList();
        backtrack(list, new ArrayList(), n, k, 1);
        return list;
    }
    
    private void backtrack(List<List<Integer>> list, List<Integer> tempList, int n, int k, int start){
        if (k == 0){
            list.add(new ArrayList(tempList));
        }else {
            for (int i = start; i <= n; i++){   // i <= n because we need the nth number
                tempList.add(i);
                backtrack(list, tempList, n, k-1, i+1);
                tempList.remove(tempList.size()-1);
            }   
        }
    }
}
```

## How does the variable `"start"` work?
"start" works as a flag in the loop. If "start" doesn't exceed the condition, a new item will be added to the `tempList`. If not, the last inserted item will be deleted from the `tempList` (`tempList.remove(tempList.size()-1)`). This is the core idea of backtracking algorithm (If the program finds a condition that doesn't satisfy the criteria, it goes back to the previous version and choose another condition).

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

* [Sudoku Solver](sudoku-solver.md)