# Combination Sum II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/combination-sum-ii/description/)

Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

Each number in C may only be used once in the combination.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
For example, given candidate set [10, 1, 2, 7, 6, 1, 5] and target 8, 

## My Solution
```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> list = new ArrayList();
        Arrays.sort(candidates);
        backtrack(list, new ArrayList(), candidates, 0, target);
        return list;
    }
    
    public void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] candidates, int start, int remain){
        if (remain < 0){return;}
        else if (remain == 0 && list.contains(tempList) == false){list.add(new ArrayList(tempList));}
        else {
            for (int i = start; i < candidates.length; i++){
                tempList.add(candidates[i]);
                backtrack(list, tempList, candidates, i+1, remain - candidates[i]);
                tempList.remove(tempList.size()-1);
            }
        }
    }
}
```

## Improvement
Instead of checking if the item exists in the list `else if (remain == 0 && list.contains(tempList) == false)`, we can just skip the duplicates.
## Rewrite the `backtrack` method:

```Java
public void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] candidates, int start, int remain){
    if (remain < 0){return;}
    else if (remain == 0){list.add(new ArrayList(tempList));}
    else {
        for (int i = start; i < candidates.length; i++){
            /* Since the array is sorted, just check with the previous element to see if it is a duplicate. */
            if(i > start && nums[i] == nums[i-1]) continue; // skip duplicates
            tempList.add(candidates[i]);
            backtrack(list, tempList, candidates, i+1, remain - candidates[i]);
            tempList.remove(tempList.size()-1);
        }
    }
}
```

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)

* [Combination](combination.md)