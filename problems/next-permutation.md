# Next Permutation - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/next-permutation/description/)

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.
1,2,3 → 1,3,2

3,2,1 → 1,2,3

1,1,5 → 1,5,1

## My Solution
```java
class Solution {
    public void nextPermutation(int[] nums) {
        int i = nums.length - 2;
        while (i >= 0 && nums[i+1] <= nums[i])
            i--;
        
        if (i >= 0){
            int j = nums.length - 1;
            while (j >= 0 && nums[j] <= nums[i])
                j--;
            swap(nums, i, j);
        }
        reverse(nums, i+1);
    }
    
    private void swap(int[] nums, int i, int j){
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
    
    private void reverse(int nums[], int i){
        int c = i, j = nums.length - 1;
        while (c < j) {
            swap(nums, c, j);
            c++;
            j--;
        }
    }
}
```

## Complexity
O(n)