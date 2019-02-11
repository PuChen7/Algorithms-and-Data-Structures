# Find Smallest Letter Greater Than Target - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

## Description
 Given a list of sorted characters letters containing only lowercase letters, and given a target letter target, find the smallest element in the list that is larger than the given target.

Letters also wrap around. For example, if the target is target = 'z' and letters = ['a', 'b'], the answer is 'a'. 

## Thinking & Notes
* Linear: scan through array, if found char > target, return char. if not found, return the first char in array.
* Binary Search:  If letters[mi] <= target, then we must insert it in the interval [mi + 1, hi]. Otherwise, we must insert it in the interval [lo, mi].

## Solution - Linear
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        for (char c : letters)
            if (c > target) return c;
        return letters[0];
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Binary Search
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int lo = 0, hi = letters.length;
        while (lo < hi){
            int mid = lo + (hi - lo)/2;
            if (letters[mid] <= target) lo = mid + 1;
            else hi = mid;
        }
        return letters[lo % letters.length];
    }
}
```
### Complexity
* Time Complexity: O(logn)
* Space Complexity: O(1)

