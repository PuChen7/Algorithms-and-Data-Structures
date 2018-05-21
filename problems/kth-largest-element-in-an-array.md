# Kth Largest Element in an Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

Example 1:

Input: [3,2,1,5,6,4] and k = 2

Output: 5

# Solution - Sorting
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length-k];
    }
}
```
## Complexity
Time Complexity: O(nlog(n))

# Solution - using PriorityQueue
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> q = new PriorityQueue<>();
        
        for (int val : nums){
            q.offer(val);   // offer() return false when fail to add, add() throw exception
            if (q.size() > k) q.poll(); // remove greater values when reach k
        }
        return q.peek();
    }
}
```
## Complexity
* Time Complexity: O(N lg K) - iterate over the whole input
* Space Complexity O(K)

# Soluition - Selection Algorithm
```java

```

