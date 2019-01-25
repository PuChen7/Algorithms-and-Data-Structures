# Peak Index in a Mountain Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

## Description
Let's call an array A a mountain if the following properties hold:

    A.length >= 3
    
    There exists some 0 < i < A.length - 1 such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]

Given an array that is definitely a mountain, return any i such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1].

## Thinking & Notes
* General approach: iterate through the array, return `i` when `A[i]>A[i+1]`.
* Binary Search: use main logic of binary search, modify conditions.

## Solution - General approach
```java
class Solution {
    public int peakIndexInMountainArray(int[] A) {
        for (int i = 0; i < A.length-1; i++)
            if (A[i] > A[i+1]) return i;      
        return -1;
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Binary Search
```java
class Solution {
    public int peakIndexInMountainArray(int[] A) {
        int lo = 0, hi = A.length - 1;
        while (lo <= hi){
            int mid = lo + (hi - lo) / 2;
            if (A[mid] > A[mid-1] && A[mid] > A[mid+1]) return mid;
            else if (A[mid] > A[mid-1] && A[mid] < A[mid+1]) lo = mid + 1;
            else hi = mid - 1;
        }
        return -1;
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)

### Core Algorithm & Data Sructure
* Binary Search

### Any related or similar problems?
* [Find Peak Element](find-peak-element.md)
