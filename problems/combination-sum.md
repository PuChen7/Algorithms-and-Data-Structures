# Combination Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/combination-sum/description/)

Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:

All numbers (including target) will be positive integers.

The solution set must not contain duplicate combinations.

```java
public static List<List<Integer>> combinationSum(int[] nums, int target) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums);
    backtrack(list, new ArrayList<>(), nums, target, 0);
    return list;
}

private static void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, int remain, int start){
    if(remain < 0) return;
    else if(remain == 0) { 
        list.add(new ArrayList<>(tempList));
    }
    else{ 
        for(int i = start; i < nums.length; i++){
            tempList.add(nums[i]);
            backtrack(list, tempList, nums, remain - nums[i], i); 
            tempList.remove(tempList.size() - 1);
        }
    }
}
```

### Analysis

The algorithm tries all possible paths, but it immediately eliminates the bad solution in the checking process.

## Implementation:

```Java
import java.util.*;
public class Test {
	public static void main(String args[]) {
		int[] nums = {1,2,3,4,5};
		List<List<Integer>> arr = new ArrayList<List<Integer>>();		
		arr = combinationSum(nums, 6);
		
	}
	public static List<List<Integer>> combinationSum(int[] nums, int target) {
	    List<List<Integer>> list = new ArrayList<>();
	    Arrays.sort(nums);
	    backtrack(list, new ArrayList<>(), nums, target, 0);
	    return list;
	}

	private static void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums, int remain, int start){
	    if(remain < 0) return;
	    else if(remain == 0) { 
	    		list.add(new ArrayList<>(tempList));
	    		System.out.println(tempList);
	    }
	    else{ 
	        for(int i = start; i < nums.length; i++){
	            tempList.add(nums[i]);
	            backtrack(list, tempList, nums, remain - nums[i], i); // not i + 1 because we can reuse same elements
	            tempList.remove(tempList.size() - 1);
	        }
	    }
	}
}
```
## Output of the tempList when `remain == 0`: 
`[1, 1, 1, 1, 1, 1]
[1, 1, 1, 1, 2]
[1, 1, 1, 3]
[1, 1, 2, 2]
[1, 1, 4]
[1, 2, 3]
[1, 5]
[2, 2, 2]
[2, 4]
[3, 3]`

### Backtracking problems
See other backtrack problems:

* [Combination Sum II](combination-sum2.md)

* [Combination Sum III](combination-sum3.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)

* [Combination](combination.md)

* [Sudoku Solver](sudoku-solver.md)