# Maximum Length of Pair Chain - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/maximum-length-of-pair-chain/)

## Description
 You are given n pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair (c, d) can follow another pair (a, b) if and only if b < c. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order. 

## Thinking & Notes
* DP: 
  - sort
  - consider `dp[i]` as the end for each iteration
  - compare `dp[i]` and `dp[j]`, when criteria satisfied, store current length of sequence in dp[i]
  
* Greedy
  - note: the `sort` is different, dp sort by `first val`, greedy sort by `second val`

## Solution - DP
```java
class Solution {
    public int findLongestChain(int[][] pairs) {
        Arrays.sort(pairs, (a, b) -> (a[0] - b[0]));
        int[] dp = new int[pairs.length];
        Arrays.fill(dp, 1);
        for (int i = 1; i < pairs.length; i++){
            for (int j = 0; j < i; j++){
                if (pairs[j][1] < pairs[i][0])
                    dp[i] = Math.max(dp[i], dp[j] + 1);
            }
        }
        
        int res = 0;
        for (int n : dp) res = Math.max(res, n);
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n)

## Solution - DP
```java
class Solution {
    public int findLongestChain(int[][] pairs) {
        Arrays.sort(pairs, (a, b) -> (a[1] - b[1]));
        int curr = Integer.MIN_VALUE, res = 0;
        for (int n[] : pairs){
            if (n[0] > curr){
                res++;
                curr = n[1];
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(n)

