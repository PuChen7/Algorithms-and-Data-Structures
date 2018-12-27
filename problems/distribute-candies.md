# Distribute Candies - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/distribute-candies/)

Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain. 

## Solution
```java
class Solution {
    public int distributeCandies(int[] candies) {
        Set<Integer> set = new HashSet<Integer>(candies.length);
        for (int c : candies) set.add(c);
        return Math.min(set.size(), candies.length/2);
    }
}
```
