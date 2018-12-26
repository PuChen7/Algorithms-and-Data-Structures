# Contains Duplicate - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/contains-duplicate/)

Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

Example 1:

Input: [1,2,3,1]

Output: true

## Solution
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        if (nums == null) return false;
        HashSet set = new HashSet();
        
        for (int item : nums){
            if (set.contains(item)) return true;
            set.add(item);
        }
        return false;
    }
}
```
