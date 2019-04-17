# Valid Perfect Square - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-perfect-square/)

## Description
Given a positive integer num, write a function which returns True if num is a perfect square else False.

## Thinking & Notes
* Math: A square number is 1+3+5+7+...
* Binary Search: range: `[0,num]`. use `long` to prevent `mid*mid` overflow.

## Solution - Math
```java
class Solution {
    public boolean isPerfectSquare(int num) {
        int i = 1;
        while (num > 0) {
            num -= i;
            i += 2;
        }
        return num == 0;
    }
}
```
#### Complexity
* Time Complexity: O(sqrt(n))
* Space Complexity: O(1)

## Solution - Binary Search
```java
class Solution {
    public boolean isPerfectSquare(int num) {
        int lo = 0, hi = num;
        while (lo <= hi) {
            long mid = lo + (hi - lo)/2;
            if (mid*mid == num) return true;
            else if (mid*mid > num) hi = (int) mid - 1;
            else lo = (int) mid + 1;
        }
        return false;
    }
}
```
#### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)
