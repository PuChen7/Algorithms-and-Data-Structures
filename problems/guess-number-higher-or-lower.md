# Guess Number Higher or Lower - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/guess-number-higher-or-lower/)

## Description
We are playing the Guess Game. The game is as follows:

I pick a number from 1 to n. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API guess(int num) which returns 3 possible results (-1, 1, or 0):

## Thinking & Notes
* Basic Binary Search

## Solution - Binary Search
```java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int lo = 1, hi = n;
        while (lo <= hi){
            int mid = lo + (hi - lo) / 2;
            int outcome = guess(mid);
            if (outcome == -1) mid = hi = mid - 1;
            else if (outcome == 1) lo = mid + 1;
            else return mid;
        }
        return -1;
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)

### Core Algorithm & Data Sructure
* Binary Search
