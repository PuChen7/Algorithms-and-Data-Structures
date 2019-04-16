# Kth Smallest Element in a Sorted Matrix - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

## Description
Given a n x n matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.

Note that it is the kth smallest element in the sorted order, not the kth distinct element. 

## Thinking & Notes
* PriorityQueue: use `PriorityQueue` to keep `k` smallest items.

## Solution - PriorityQueue
```java
class Solution {
    public int kthSmallest(int[][] matrix, int k) {
        PriorityQueue<Integer> heap = new PriorityQueue<Integer>((n1,n2) -> n2 - n1);
        
        for (int i = 0; i < matrix.length; i++){
            for (int j = 0; j < matrix[i].length; j++){
                heap.add(matrix[i][j]);
                if (heap.size() > k) heap.poll();
            }
        }
        return heap.poll();
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(k)

### Core Algorithm & Data Sructure
* PriorityQueue

### Any related or similar problems?
* [Top K Frequent Elements](top-k-frequent-elements.md)
