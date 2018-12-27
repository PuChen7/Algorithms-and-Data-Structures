# Intersection Of Two Arrays II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

Given two arrays, write a function to compute their intersection.

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]

Output: [2,2]

## Solution
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        ArrayList<Integer> resList = new ArrayList<Integer>();
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        // get all letter occurrences
        for (int item : nums1){
            if (map.containsKey(item))
                map.put(item, map.get(item)+1);
            else
                map.put(item, 1);
        }
        
        for (int item : nums2){
            if (map.containsKey(item) && map.get(item) > 0){
                resList.add(item);
                map.put(item, map.get(item)-1);
            }
        }
        
        // convert to array
        int[] res = new int[resList.size()];
        int i = 0;
        for (int item : resList){
            res[i++] = item;
        }
        
        return res;
    }
}
```
