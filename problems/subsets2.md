# Subsets II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/subsets-ii/description/)

Given a collection of integers that might contain duplicates, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

## My Solution
```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> list = new ArrayList();
        Arrays.sort(nums);
        backtrack(list, new ArrayList(), nums, 0);
        return list;
    }
    
    public void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] nums, int start){
        list.add(new ArrayList(tempList));
        for (int i = start; i < nums.length; i++){
            /* skip the duplicate */
            if (i > start && nums[i] == nums[i-1]){continue;}
            tempList.add(nums[i]);
            backtrack(list, tempList, nums, i+1);
            tempList.remove(tempList.size()-1);
        }
    }
}
```

## Implementation
Input {1,2,2}

Sample Output:

`[[],[1],[1,2],[1,2,2],[2],[2,2]]`

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Subsets](subsets.md)