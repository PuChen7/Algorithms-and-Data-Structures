# Four Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/4sum/description/)

Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note: The solution set must not contain duplicate quadruplets.

For example, given array S = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]

## My Solution
```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> result = new LinkedList();
        if (nums.length < 4) return result;
        Arrays.sort(nums);
        
        int max = nums[nums.length-1];
        int currNum;
        if (4 * nums[0] > target || 4 * max < target) return result;
        
        for (int i = 0; i < nums.length; i++){
            currNum = nums[i];
            if (i > 0 && currNum == nums[i-1]){continue;}   // skip duplicates
            if (currNum + 3*nums[nums.length-1] < target){continue;}    // too small
            if (4 * currNum > target){break;}   // too large
            if (4 * currNum == target){     // boundary: no need to go further
                if (i + 3 < nums.length && nums[i+3] == currNum){  // if there's four same numbers can add to target
                    result.add(Arrays.asList(currNum, currNum, currNum, currNum));
                }
                break;
            }
            threeSum(target-currNum, i+1, nums.length-1, nums, result, currNum);
        }
        return result;
    }
    
    public void threeSum(int target, int lo, int hi, int[] nums, List<List<Integer>> result, int curr){
        if (lo + 1 >= hi){return;}
        
        if (3 * nums[lo] > target || 3 * nums[hi] < target){return;}
        
        for (int i = lo; i < hi-1; i++){
            int currNum = nums[i];
            if (i > lo && currNum == nums[i-1]){continue;}   // skip duplicates
            if (currNum + 2*nums[nums.length-1] < target){continue;}    // too small
            if (3 * currNum > target){break;}   // too large
            if (3 * currNum == target){     // boundary: no need to go further
                if (i + 1 < nums.length && nums[i+2] == currNum){  // if there's four same numbers can add to target
                    result.add(Arrays.asList(curr, currNum, currNum, currNum));
                }
                break;
            }
            twoSum(target-currNum, i+1, nums.length-1, nums, result, currNum, curr);
        }
    }
    
    public void twoSum(int target, int lo, int hi, int[] nums, List<List<Integer>> result, int curr1, int curr2){
        if (lo >= hi){return;}
        
        if (2 * nums[lo] > target || 2 * nums[hi] < target){return;}
        
        int i = lo, j = hi, sum, x;
        while (i < j){
            sum = nums[i] + nums[j];
            if (sum == target){
                result.add(Arrays.asList(nums[i], nums[j], curr1, curr2));
                 // while (i<j && nums[i] == nums[i+1]) i++;
                // while (i<j && nums[j] == nums[j-1]) j--;
                x = nums[i];
                while (++i < j && x == nums[i]) // avoid duplicate
                    ;
                x = nums[j];
                while (i < --j && x == nums[j]) // avoid duplicate
                    ;
            }
            if (sum < target)
				i++;
			if (sum > target)
				j--;
        }
        return;
    }
}
```