# Majority Element - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/majority-element/description/)

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

## My Solution
```java
class Solution {
    public int majorityElement(int[] nums) {
        if (nums.length == 1)
            return nums[0];
        
        HashMap<Integer, Integer> map = new HashMap<>();
        int m = nums.length/2;
        for (int i = 0; i < nums.length; i++){
            if (map.containsKey(nums[i])){
                if (map.get(nums[i]) >= m)
                     return nums[i];
                map.put(nums[i], map.get(nums[i])+1);
                continue;
            } else {
                map.put(nums[i], 1);                
            }
        }
        return -1;
    }
}
```

## Complexity
Time Complexity: O(n)

Using HashMap to iterate nums. Inserting takes O(1) every time.

Space Complexity: O(n)