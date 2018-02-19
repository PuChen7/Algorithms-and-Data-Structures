# Combination Sum III - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/combination-sum-iii/description/)

Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.


Example 1:

Input: k = 3, n = 7

Output:

[[1,2,4]]

Example 2:

Input: k = 3, n = 9

Output:

[[1,2,6], [1,3,5], [2,3,4]]

## My Solution
```java
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> list = new ArrayList();
        backtrack(list, new ArrayList(), k, n, 1);
        return list;
    }
    
    private void backtrack(List<List<Integer>> list, List<Integer> tempList, int k, int n, int start){
        if (k == 0 && n == 0){
            list.add(new ArrayList(tempList));
        } else {
            for (int i = start; i <= 9; i++){   // remember i <= 9 because we can only use 1 to 9
                tempList.add(i);
                backtrack(list, tempList, k-1, n-i, i+1);
                tempList.remove(tempList.size()-1);
            }
        }
    }
}
```

## Analysis
This problem combines `Combination Sum` and `Combination`. 

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)

* [Combination](combination.md)