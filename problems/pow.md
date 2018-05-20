# Pow(x, n) - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/powx-n/description/)

Implement pow(x, n), which calculates x raised to the power n (xn).

Example 1:

Input: 2.00000, 10

Output: 1024.00000

Example 2:

Input: 2.10000, 3

Output: 9.26100

Example 3:

Input: 2.00000, -2

Output: 0.25000

Explanation: 2-2 = 1/22 = 1/4 = 0.25

Note:

-100.0 < x < 100.0
n is a 32-bit signed integer, within the range [−231, 231 − 1]

```java 
class Solution {
    public double myPow(double x, int n) {
        // check for edge cases
        if(x==0 || x > Integer.MAX_VALUE || x < Integer.MIN_VALUE)
            return 0;
        if (n == 0) return 1;
        if (n < 0){
            x = 1/x;
            n = -n;
        }
        if (n % 2 == 0) 
            return myPow(x*x, n/2);
        else 
            return x*myPow(x*x, n/2);
    }
}
```

## Consider
This problem has many special cases:
* when n is `0`, return 1
* when n is `negative`, need to convert x to 1/x, and then set n = -n
* when `x > Integer.MAX_VALUE` or `x < Integer.MIN_VALUE` or `x == 0`, return 0

## Complexity
Time Complexity: O(log(n)), because each iteration divide n to half.
