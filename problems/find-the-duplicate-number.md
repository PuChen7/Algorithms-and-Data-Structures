# Find the Duplicate Number - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-the-duplicate-number/description/)

Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

## My Solution - Version I
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

Time Complexity: O(n)
