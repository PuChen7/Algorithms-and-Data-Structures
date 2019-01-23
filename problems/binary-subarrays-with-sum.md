# Binary Subarrays With Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-subarrays-with-sum/)

## Description
In an array A of 0s and 1s, how many non-empty subarrays have sum S?

Example 1:

Input: A = [1,0,1,0,1], S = 2

Output: 4

Explanation: 
The 4 subarrays are bolded below:
[1,0,1,0,1], 
[1,0,1,0,1], 
[1,0,1,0,1], 
[1,0,1,0,1]

## Thinking & Notes
* Brute Force: caculate sum for every sub-array combinations. if sum == S, res++
 
## Solution - Brute Force
```java
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        int res = 0;
        for (int i = 0; i < A.length; i++){
            int sum = 0;
            for (int j = i; j < A.length; j++){
                sum += A[j];
                if (sum == S) res++;
            }
        }
        return res;
    }
}
```
### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)

### Core Algorithm & Data Sructure

### More About this Algorithm & Data Structure?

### Any related or similar problems?
