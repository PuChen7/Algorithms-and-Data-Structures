# Merge Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/merge-sorted-array/description/)

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:

The number of elements initialized in nums1 and nums2 are m and n respectively.

You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.

# Solution
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        // keep two pointers at the last element of nums1 and nums2
        int a = m-1, b = n-1, t = m+n-1;
        while (a >= 0 && b >= 0){
            // if nums1 has greater number, then move it to the index t
            if (nums1[a] > nums2[b]) nums1[t--] = nums1[a--];
            else nums1[t--] = nums2[b--];   // otherwise move nums2 element to index t
        }
        // check if all elements in nums2 have been added to the nums1
        while (b >= 0){
            nums1[t--] = nums2[b--];
        }
    }
}
```
## Complexity
Time Complexity: O(m+n)