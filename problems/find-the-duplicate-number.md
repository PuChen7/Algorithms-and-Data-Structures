# Find the Duplicate Number - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-the-duplicate-number/description/)

## Description
Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

## Thinking & Notes
* Linked List Cycle: similar to linked list cycle problem. 
* Binary Search: 

At first the search space is `numbers` between 1 to n. 
Each time select a number `mid` and count all the numbers `equal to or less` than `mid`. 
Then if the `count` is more than mid, the search space will be `[1 mid]` otherwise `[mid+1 n]`. 
I do this until search space is only one number.

Let's say n=10 and I select mid=5. Then I count all the numbers in the array which are less than equal mid. If the there are more than 5 numbers that are less than 5, then by [Pigeonhole Principle](https://en.wikipedia.org/wiki/Pigeonhole_principle) one of them has occurred more than once. So I shrink the search space from `[1 10]` to `[1 5]`. Otherwise the duplicate number is in the second half so for the next step the search space would be `[6 10]`.

## Solution - Linked List Cycle
```java
class Solution {
    public int findDuplicate(int[] nums) {
        int fast = nums[0];
        int slow = nums[0];
        do{
            fast = nums[nums[fast]];
            slow = nums[slow];
        }while(fast != slow);
        
        int tmp = nums[0];
        while (tmp != slow){
            tmp = nums[tmp];
            slow = nums[slow];
        }
        return slow;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Binary Search
```java
class Solution {
    public int findDuplicate(int[] nums) {
        int lo = 0, hi = nums.length -1;
        while (lo <= hi) {
            int count = 0;
            int mid = lo + (hi - lo) / 2;
            for (int num : nums) {
                if (num <= mid) count++;   
            }
            if (count <= mid) lo = mid + 1;
            else hi = mid - 1;
        }
        return lo;
    }
}
```
#### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(n)

### Core Algorithm & Data Sructure
* Binary Search (not sorted. search in range)
* Linked List Detect Cycle

### Any related or similar problems?
* [Linked List Cycle](linked-list-cycle.md)
* [Kth Smallest Element in a Sorted Matrix](kth-smallest-element-in-a-sorted-matrix.md) - Used similar Binary search idea(search in range)
