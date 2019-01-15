# Contiguous Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/contiguous-array/)

## Description
Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

Example 1:

Input: [0,1]

Output: 2

Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.

### Thinking & Notes
* Brute force: check every combination and count zeros and ones. O(n^2). not accepted due to exceed time limit. 
* HashMap + Sum: change all `0` to `-1`. check if map contains the key

## Solution
```java
class Solution {
    public int findMaxLength(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) if (nums[i] == 0) nums[i] = -1;
        
        map.put(0, -1);     // why? 
        int currMax = 0, sum = 0;
        for (int i = 0; i < nums.length; i++){
            sum += nums[i];
            if (map.containsKey(sum))
                currMax = Math.max(currMax, i - map.get(sum));
            else
                map.put(sum, i);
        }
        return currMax;
    }
}
```

### Complexity
* Time: O(n)
* Space: O(n)
