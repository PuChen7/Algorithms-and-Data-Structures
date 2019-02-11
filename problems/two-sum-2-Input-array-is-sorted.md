# Two Sum II - Input array is sorted - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Description

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

## Thinking & Notes
* Brute Force: two loops to check every number in the array. 
* Binary Search: basic binary search. if sum > target, hi--, else lo++.
## Solution - Brute Force
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int[] res = new int[2];
        for (int i = 0; i < numbers.length; i++){
            res[0] = i+1;
            for (int j = i+1; j < numbers.length; j++){
                if (target - numbers[i] == numbers[j]){
                    res[1] = j+1;
                    return res;
                }
            }
        }
        return new int[2];
    }
}
```
### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)

## Solution - Binary Search
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int[] res = new int[2];
        if (numbers == null || numbers.length < 2) return res;
        int lo = 0, hi = numbers.length - 1;
        while (lo < hi){
            if (numbers[lo]+numbers[hi] == target){
                res[0] = lo + 1;
                res[1] = hi + 1;
                break;
            } else if (numbers[lo]+numbers[hi] < target){
                lo++;
            } else {
                hi--;
            }
        }
        return res;
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)
