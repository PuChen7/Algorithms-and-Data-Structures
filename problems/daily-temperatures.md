# Daily Temperatures - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/daily-temperatures/)

## Description
 Given a list of daily temperatures T, return a list such that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.

For example, given the list of temperatures T = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0]. 

## Thinking & Notes
* Brute force: for every temperature, compare with the rest of array.

## Solution - Brute Force
```java
class Solution {
    public int[] dailyTemperatures(int[] T) {
        int[] res = new int[T.length];
        
        for (int i = 0; i < T.length; i++){
            int temperature = T[i];
            for (int j = i+1; j < T.length; j++){
                if (T[j] > temperature) {
                    res[i] = j-i;
                    break;
                }
            }
        }
        return res;
    }
}
```
### Complexity
* Time: ? (n*n-1)+(n*n-2)+...+(n*1)
* Space: O(1)

