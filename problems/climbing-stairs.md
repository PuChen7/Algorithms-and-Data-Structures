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
