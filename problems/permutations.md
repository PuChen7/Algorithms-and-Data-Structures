# Permutations - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/permutations/description/)

Given a collection of distinct numbers, return all possible permutations.

For example,
[1,2,3] have the following permutations:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]

## My Solution
```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> list = new ArrayList();
        backtrack(list, new ArrayList(), nums);
        return list;
    }
    
    public void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] nums){
        if (tempList.size() == nums.length){
            list.add(new ArrayList(tempList));
        }
        for (int i = 0; i < nums.length; i++){
            if (tempList.contains(nums[i])){continue;}
            tempList.add(nums[i]);
            backtrack(list, tempList, nums);
            tempList.remove(tempList.size()-1);
        }
    }
}
```

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)