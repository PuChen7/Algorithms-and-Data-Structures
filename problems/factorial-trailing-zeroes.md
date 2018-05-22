# Factorial Trailing Zeroes - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/factorial-trailing-zeroes/description/)

Given an integer n, return the number of trailing zeroes in n!.

# Solution
```java
class Solution {
    public int trailingZeroes(int n) {
        int r = 0;
        // count how many 5 in n
        while (n > 4){
            r += (n/=5);
        }
        return r;
    }
}
```

## Explanation
10 = 2 * 5 (too many 2, so count 5)

=2 * 3 * ...* 5 ... *10 ... 15* ... * 25 ... * 50 ... * 125 ... * 250...

=2 * 3 * ...* 5 ... * (5^1*2)...(5^1*3)...*(5^2*1)...*(5^2*2)...*(5^3*1)...*(5^3*2)...

# Note
* range of input? integer overflow/underflow?
* negative?