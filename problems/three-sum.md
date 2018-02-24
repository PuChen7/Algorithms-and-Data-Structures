# Three Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/3sum/description/)

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note: The solution set must not contain duplicate triplets.

For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]

## My Solution
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);  // sort array to deal with duplicates
        List<List<Integer>> list = new LinkedList();    // why linked list?
        
        for (int i = 0; i < nums.length-2; i++){    // why i < nums.length-2? find unique TRIPLETS
            if (i == 0 || (i > 0 && nums[i] != nums[i-1])){ // note to skip the duplicate
                int lo = i + 1; // set lo to next value
                int hi = nums.length - 1;   // set hi to the last value
                int sum = 0 - nums[i];  // set sum equals to the sum of the other two values
                while (lo < hi){
                    if (nums[lo] + nums[hi] == sum){
                        list.add(Arrays.asList(nums[i], nums[lo], nums[hi]));
                        while (lo < hi && nums[lo] == nums[lo+1]) lo++; // skip all the duplicates
                        while (lo < hi && nums[hi] == nums[hi-1]) hi--; // skip all the duplicates
                        lo++; hi--; 
                    } else if (nums[lo] + nums[hi] < sum){lo++;}
                    else {hi--;}
                }
            }
        }
        return list;
    }
}
```