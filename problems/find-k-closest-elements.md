# Find K Closest Elements - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-k-closest-elements/)

## Description
Given a sorted array, two integers k and x, find the k closest elements to x in the array. The result should also be sorted in ascending order. If there is a tie, the smaller elements are always preferred. 

## Thinking & Notes
* Binary Search: 
  * say if we need to pick 4 elems, now looking at 5 elem n1, n2, n3, n4, n5
  * we need to compare two ends: diff(x, n1) and diff(x, n5), the number with bigger diff on the end will be eleminated

## Solution - 
```java
class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        List<Integer> res = new ArrayList<>();
        int lo = 0, hi = arr.length - k;
        while (lo < hi){
            int mid = lo + (hi - lo) / 2;
            if (x - arr[mid] > arr[mid+k] - x)
                lo = mid + 1; //arr[mid] is the one further away from x, eliminate range[lo, mid]
            else
                hi = mid; // arr[mid+k] is the one further away, all [mid, hi] will have simiar situation, elimiate
        }
        for (int i = lo; i < lo+k; i++){
            res.add(arr[i]);
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(log n)
* Space Complexity: O(1)
