# Search Insert Position - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/search-insert-position/description/)

Given a sorted array and a target value, return the index if the target is found. 
If not, return the index where it would be if it were inserted in order.

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;
        while(low <= high){
            int mid = (low + high) / 2;
            if (nums[mid] == target) {return mid;}
            else if (nums[mid] > target) {high = mid - 1;}
            else {low = mid + 1;}
        }
        return low;
    }
}
```

The solution's algorithm compares the target with the middle element of the array, 
then split the array into half based on the value of the element, 
and repeat this procedure until the target is found or reached the end.