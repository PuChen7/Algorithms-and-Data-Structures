# Move Zeros - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/move-zeroes/description/)

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.

Minimize the total number of operations.

## Solution I - Using ArrayList (O(n) Time Complexity, O(n) Space Complexity)
```java
class Solution {
    public void moveZeroes(int[] nums) {
       // deal with edge cases
        if (nums == null || nums.length == 1)
            return;
        
        // count the number of zeros
        int zeros = 0;
        for (int i = 0; i < nums.length; i++){
            if (nums[i] == 0)
                zeros++;
        }
        
        // get all non-zeros elements
        ArrayList<Integer> vec = new ArrayList<Integer>();
        for (int i = 0; i < nums.length; i++){
            if (nums[i] != 0)
                vec.add(nums[i]);
        }
        
        // push all zeros to the end, because vector keeps insertion order
        while (zeros != 0) {
            vec.add(0);
            zeros--;
        }
        
        // pop everything out
        for (int i = 0; i < nums.length; i++){
            nums[i] = vec.remove(0);
        }
    }
}
```

## Solution II - (O(n) Time Complexity, O(1) Space Complexity)
```java 
class Solution {
    public void moveZeroes(int[] nums) {
        // keeps the index of last non zero element
        int lastNonZero = 0;
        
        // if the number is non zero, add at lastNonZero, then increment lastNonZero
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[lastNonZero] = nums[i];
                lastNonZero++;
            }
        }
        
        // set the remaining spot to zeros
        for (int i = lastNonZero; i < nums.length; i++) {
            nums[i] = 0;
        }
    }
}
```
Worst Case: [0,0,0,...,0,1] -> Needs n-1 times to write 0

## Solution III - Optimal
```java
class Solution {
    public void moveZeroes(int[] nums) {
        // keeps the index of last non zero element
        int lastNonZero = 0;
        
        // if the number is non zero, swap
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                int tmp = nums[lastNonZero];
                nums[lastNonZero] = nums[i];
                nums[i] = tmp;
                lastNonZero++;
            }
        }
    }
}
```
O(n) Time Complexity, O(1) Space Complexity, reduced number of operations than Solution II