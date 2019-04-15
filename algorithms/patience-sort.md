# Patience Sorting

## Time Complexity: O(nlogn)
## Space Complexity: O(n)

## Algorithm
* Example: [1,3,5,2,8,4,6]
  * Form sub-arrays with:
    * Different `length`
    * Must be `incresing` order
    * [1], [1,2], [1,3,4], [1,3,5,6]
  * For every incoming number `n`:
    * if `n` > the largest tail (6), create a new sub-array of the longest length plus `n` ([1,3,5,6] + `n` = [1,3,5,6,n])
    * if `n` < the smallest tail (1), replace the smallest tail with `n`
    * if `n` in the middle, find the smallest number > `n`, then replace. (Use `Binary Search` to find since all sub-arrays are sorted)
  
  ```java
  public class Solution {
public int longestIncreasingSubsequence(int[] nums) {
    // write your code here
    if(nums.length == 0){
        return 0;
    }
    // len表示当前最长的升序序列长度（为了方便操作tails我们减1）
    int len = 0;
    // tails[i]表示长度为i的升序序列其末尾的数字
    int[] tails = new int[nums.length];
    tails[0] = nums[0];
    // 根据三种情况更新不同升序序列的集合
    for(int i = 1; i < nums.length; i++){
        if(nums[i] < tails[0]){
            tails[0] = nums[i];
        } else if (nums[i] >= tails[len]){
            tails[++len] = nums[i];
        } else {
        // 如果在中间，则二分搜索
            tails[binarySearch(tails, 0, len, nums[i])] = nums[i];
        }
    }
    return len + 1;
}

private int binarySearch(int[] tails, int min, int max, int target){
    while(min <= max){
        int mid = min + (max - min) / 2;
        if(tails[mid] == target){
            return mid;
        }
        if(tails[mid] < target){
            min = mid + 1;
        }
        if(tails[mid] > target){
            max = mid - 1;
        }
    }
    return min;
}
```
