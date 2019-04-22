# K-diff Pairs in an Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/k-diff-pairs-in-an-array/)

## Description
Given an array of integers and an integer k, you need to find the number of unique k-diff pairs in the array. 
Here a k-diff pair is defined as an integer pair (i, j), where i and j are both numbers in the array and their 
absolute difference is k. 

## Thinking & Notes
* HashMap: use map to count occurrences, so we have unique elements with counts. Only count `ele + k` so we can eliminate `ele-k`.

## Solution - HashMap
```java
class Solution {
    public int findPairs(int[] nums, int k) {
        if (nums == null || nums.length == 0 || k < 0)   return 0;
        Map<Integer, Integer> map = new HashMap<>();
        int count = 0;
        for (int n : nums) map.put(n, map.getOrDefault(n, 0) + 1);

        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (k == 0) {
                if (entry.getValue() >= 2) count++;
            } else {
                if (map.containsKey(entry.getKey() + k)) count++;
            }
        }
        return count;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
