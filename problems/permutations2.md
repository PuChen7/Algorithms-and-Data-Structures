# Permutations II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/permutations-ii/description/)

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

For example,
[1,1,2] have the following unique permutations:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]

## My Solution
```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> list = new ArrayList();
        Arrays.sort(nums);
        backtrack(list, new ArrayList(), nums, new boolean[nums.length]);
        return list;
    }
    
    public void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] nums, boolean[] visited){
        if (tempList.size() == nums.length){
            list.add(new ArrayList(tempList));
        }else {
            for (int i = 0; i < nums.length; i++){
                // why !visited[i-1]: if i is added to list || i > && i = i-1 && i-1 is added to the list
                if (visited[i] || i > 0 && nums[i] == nums[i-1] && !visited[i-1]){continue;}
                visited[i] = true;
                tempList.add(nums[i]);
                backtrack(list, tempList, nums, visited);
                tempList.remove(tempList.size()-1);
                visited[i] = false; // why set to false
            }
        }
    }
}
```

## Analysis
The difference between Permutations and Permutations II is Permutations II has duplicates.

Therefore we need to deal with the duplicate element. The program has a boolean array which records if the ith element is visited. 

The key is to filter out the second duplicate element by apply the if statement `if (visited[i] || i > 0 && nums[i] == nums[i-1] && !visited[i-1]){continue;}`. 

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Palindrome Partitioning](palindrome-partitioning.md)