# Climbing Stairs - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/climbing-stairs/)

## Description
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.

## Thinking & Notes
* Brute force:
  - In this brute force approach we take all possible step combinations i.e. 1 and 2, at every step. 
  At every step we are calling the function `climb` for step 1 and 2, and return the sum of returned values of both functions.
  - climb(i,n)=(i+1,n)+climb(i+2,n)
  
* Brute force with mem
  - we can keep an array to store visited steps. Just need to fill array, and then the last index is the res.
  
* DP
- One can reach i step in one of the two ways:
  - Taking a `single` step from (i−1) step.
  - Taking a step of `2` from (i−2) step.
- So, the total number of ways to reach i is equal to sum of ways of reaching (i−1) step and ways of reaching (i−2) step.
- Let `dp[i]` denotes the number of ways to reach on `i` step:
- `dp[i]=dp[i−1]+dp[i−2]`
  
## Solution - Brute force (Time Limit Exceeded)
```java
class Solution {
    public int climbStairs(int n) {
        // brute force: climb(i,n)=(i+1,n)+climb(i+2,n)
        return climb(0, n);
    }
    
    private int climb(int i, int n){
        if (i > n) return 0;
        if (i == n) return 1;
        return climb(i + 1, n) + climb(i + 2, n);
    }
}
```
#### Complexity
* Time Complexity: O(2^n)
* Space Complexity: O(1)

## Solution - Brute force with mem
```java
class Solution {
    public int climbStairs(int n) {
        int[] mem = new int[n+1];
        return climb(0, n, mem);
    }
    
    private int climb(int i, int n, int[] mem){
        if (i > n) return 0;
        if (i == n) return 1;
        if (mem[i] > 0) return mem[i];
        mem[i] = climb(i + 1, n, mem) + climb(i + 2, n, mem);
        return mem[i];
    }
    // why O(n)? because everytime we see if mem[i] is already filled. This prevent extra recursion.
    // just need to fill the array
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

## Solution - DP
```java
class Solution {
    public int climbStairs(int n) {
        if (n == 1) return 1;
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; i++){
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
