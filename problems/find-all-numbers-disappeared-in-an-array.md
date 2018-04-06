# Two Sum II - Input array is sorted - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9

Output: index1=1, index2=2

## My Solution - Version I
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int[] res = new int[2];
        if (numbers == null || numbers.length < 2) return numbers;
        int lo = 0;
        int hi = numbers.length - 1;
        while (lo < hi){
            if (target == numbers[lo] + numbers[hi]){
                res[0] = lo + 1;
                res[1] = hi + 1;
                return res;
            } else if (target > numbers[lo] + numbers[hi]) lo++;
            else hi--;
        }
        return res;
    }
}
```

Time Complexity: O(n)