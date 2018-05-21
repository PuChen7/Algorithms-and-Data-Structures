# Missing Number - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/missing-number/description/)

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

## Solution - Sorting
```java
class Solution {
    public int missingNumber(int[] nums) {
        Arrays.sort(nums);  // sort array first
        // check if 0 exists
        if (nums[0] != 0) return 0;
        // check last element
        if (nums[nums.length-1] != nums.length) return nums.length;
        // look for missing num within (0, n)
        for (int i = 1; i < nums.length; i++){
            if (i != nums[i])
                return i;
        }
        return -1;  // missing number not found
    }
}
```
### Complexity
Time Complexity: O(nlog(n)) because of sorting

Space Complexity O(1). Could be O(n) if modifying the array is not allowed.

## Solution - HashSet
```java
class Solution {
    public int missingNumber(int[] nums) {
        if (nums == null) return -1;
        
        // create a hashset and then add all elements in nums to the set
        Set<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++){
            set.add(nums[i]);
        }
        
        // check if every i appears in set, if not, return i
        int expectedNum = nums.length+1;
        for (int i = 0; i < expectedNum; i++){
            if (!set.contains(i))
                return i;
        }
        return -1;  // not found
    }
}
```

## Solution - Gauss' Formula
```java
class Solution {
    public int missingNumber(int[] nums) {
        int sum = (nums.length*(nums.length+1))/2;
        for (int i = 0; i < nums.length; i++)
            sum -= nums[i];
        return sum;
    }
}
```
### Complexity
Time Complexity: O(n)
