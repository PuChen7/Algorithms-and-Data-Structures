# Longest Harmonious Subsequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-harmonious-subsequence/)

We define a harmonious array is an array where the difference between its maximum value and its minimum value is exactly 1.

Now, given an integer array, you need to find the length of its longest harmonious subsequence among all its possible subsequences.

Example 1:

Input: [1,3,2,2,5,2,3,7]

Output: 5

Explanation: The longest harmonious subsequence is [3,2,2,2,3].

## Solution
```java
class Solution {
    public int findLHS(int[] nums) {
        if (nums == null) return 0;
        int res = 0;
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        // get numbers and occurrences
        for (int item : nums) map.put(item, map.getOrDefault(item, 0) + 1);
        
        for (int key : map.keySet()){
            if (map.containsKey(key+1)){
                int tempSeq = map.get(key) + map.get(key+1);
                res = Math.max(tempSeq, res);
            }
        }
        return res;
    }
}
```
