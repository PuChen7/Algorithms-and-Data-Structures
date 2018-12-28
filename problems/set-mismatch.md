# Set Mismatch - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/set-mismatch/)

 The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.

Example 1:

Input: nums = [1,2,2,4]

Output: [2,3]

## Solution - Clean Code
```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int correctSum = getCorrectSum(nums.length);
        int actualSum = getActualSum(nums);
        int dup = findDuplicateNumber(nums);
        int missingNumber = findMissingNumber(correctSum, actualSum, dup);
        return new int[] {dup, missingNumber};
    }
    
    private int getCorrectSum(int n){
        return ((1+n)*n)/2;
    }
    
    private int getActualSum(int[] nums){
        int sum = 0;
        for (int number : nums) sum += number;
        return sum;
    }
    
    private int findDuplicateNumber(int[] nums){
        HashSet<Integer> set = new HashSet<>();
        for (int item : nums)
            if (!set.add(item)) return item;
        return -1;
    }
    
    private int findMissingNumber(int correctSum, int actualSum, int dup){
        return correctSum - actualSum + dup;
    }
}
```
