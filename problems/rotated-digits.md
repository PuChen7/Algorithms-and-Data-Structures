# Rotated Digits - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/rotated-digits/)

## Description
X is a good number if after rotating each digit individually by 180 degrees, we get a valid number that is different from X.  Each digit must be rotated - we cannot choose to leave it alone.

A number is valid if each digit remains a digit after rotation. 0, 1, and 8 rotate to themselves; 2 and 5 rotate to each other; 6 and 9 rotate to each other, and the rest of the numbers do not rotate to any other number and become invalid.

Now given a positive number N, how many numbers X from 1 to N are good?

## Thinking & Notes
* Brute force: for each number, check each digits. Used hard-coded numbers
* Without hard-coding
* Dynamic Programming: use array with `N+1` size. 
  - dp[i] = 0, invalid number
  - dp[i] = 1, valid and same number
  - dp[i] = 2, valid and different number

## Solution - Brute force
```java
class Solution {
    public int rotatedDigits(int N) {
        int res = 0;
        for (int i = 1; i <= N; i++){
            res += isValid(i);
        }
        return res;
    }
    
    private int isValid(int n){
        String s = String.valueOf(n);
        StringBuilder sb = new StringBuilder();
        for (char c : s.toCharArray()){
            if (c == '3' || c == '4' || c == '7') return 0;
            else if (c == '2') sb.append('5');
            else if (c == '5') sb.append('2');
            else if (c == '6') sb.append('9');
            else if (c == '9') sb.append('6');
            else sb.append(c);
        }
        return sb.toString().equals(s) ? 0 : 1;
    }
}
```
#### Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(m)

## Solution - Without hard-coding
```java
class Solution {
    public int rotatedDigits(int N) {
        int count = 0;
        for (int i = 1; i <= N; i ++) {
            if (isValid(i)) count ++;
        }
        return count;
    }
    
    public boolean isValid(int N) {
        /*
         Valid if N contains ATLEAST ONE 2, 5, 6, 9
         AND NO 3, 4 or 7s
         */
        boolean validFound = false;
        while (N > 0) {
            if (N % 10 == 2) validFound = true;
            if (N % 10 == 5) validFound = true;
            if (N % 10 == 6) validFound = true;
            if (N % 10 == 9) validFound = true;
            if (N % 10 == 3) return false;
            if (N % 10 == 4) return false;
            if (N % 10 == 7) return false;
            N = N / 10;
        }
        return validFound;
    }
}
```

## Solution - DP
```java
class Solution {
    public int rotatedDigits(int N) {
        int[] dp = new int[N+1];
        int res = 0;
        for (int i = 0; i <= N; i++){
            if (i < 10){
                if (i == 0 || i == 1 || i == 8) dp[i] = 1;
                if (i == 2 || i == 5 || i == 6 || i == 9){
                    dp[i] = 2;
                    res++;
                }
            } else {
                int a = dp[i / 10], b = dp[i % 10]; // split number, if i has more than 1 digit, all sub digits are visited. only need to care about new digit
                if (a == 1 && b == 1) dp[i] = 1;    // this case will only go into this block, will not go into else if
                else if (a >= 1 && b >= 1){
                    dp[i] = 2;
                    res++;
                }
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n+1)
