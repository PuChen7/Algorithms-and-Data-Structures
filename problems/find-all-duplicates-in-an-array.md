# Find All Duplicates in an Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/)

Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements that appear twice in this array.

Could you do it without extra space and in O(n) runtime?

```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        List<Integer> arrList = new ArrayList<>();
        
        for (int i = 0; i < nums.length; i++){
            int index = Math.abs(nums[i]) - 1;
            if (nums[index] < 0)
                arrList.add(index + 1);
            nums[index] = -nums[index];
        }
        return arrList;
    }
}
```

This solution is provided by @YUXINCAO on LeetCode.