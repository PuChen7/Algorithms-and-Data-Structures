# Intersection Of Two Arrays - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/)

iven two arrays, write a function to compute their intersection.

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]

Output: [2]

## Solution
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet set = new HashSet();
        HashSet<Integer> res = new HashSet<Integer>();
        
        for (int item : nums1)
            set.add(item);
        
        for (int item : nums2){
            if (set.contains(item))
                res.add(item);
        }
        
        int[] resArr = new int[res.size()];
        
        int i = 0;
        for (int item : res)
            resArr[i++] = item;
        
        return resArr;
    }
}
```
