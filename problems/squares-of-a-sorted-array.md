# Squares of a Sorted Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/)

## Description
Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

## Thinking & Notes
* Sorting: traverse array. for each `num = num * num`. sort the array.
* Two Pointers: this is similar to `merging two sorted array`. 
If compare both ends with `Math.abs()`, the array will be two sorted parts: `decreasing,increasing`.

## Solution - Sorting
```java
class Solution {
    public int[] sortedSquares(int[] A) {
        for (int i = 0; i < A.length; i++)
            A[i] = A[i] * A[i];
        Arrays.sort(A);
        return A;
    }
}
```
#### Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(1)

## Solution - Two Pointers
```java
class Solution {
    public int[] sortedSquares(int[] A) {
        int n = A.length;
        int[] res = new int[n];
        int i = 0, j = n -1;
        for (int index = n-1; index >= 0; index--){
            if (Math.abs(A[j]) > Math.abs(A[i])){
                res[index] = A[j] * A[j];
                j--;
            } else {
                res[index] = A[i] * A[i];
                i++;
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
