#  Count Binary Substrings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/count-binary-substrings/)

## Description
Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.

Substrings that occur multiple times are counted the number of times they occur.

## Thinking & Notes
* Group: we can group `0` and `1` by counting. For example: `00111`, we can group to `[2,3]`. 
then observe `00111` can only form two substrings: `01`, and `0011`, which is `2` of `[2,3]`.
so we can sum up all Math.min of group array.

* Without storing group: instead of storing group array, we can sum up during iteration. 
keep `curr` to count current substring, for example: `11100`, we use `curr` count `111` which is `3`, 
then `prev = curr`, we keep count of `111` to `prev`, then use `curr` to count `00`. then we get min of `3,2`.   

## Solution - Group
```java
class Solution {
    public int countBinarySubstrings(String s) {
        int t = 0;
        int[] group = new int[s.length()];
        group[0] = 1;
        for (int i = 1; i < s.length(); i++){
            if (s.charAt(i-1) != s.charAt(i))
                group[++t] = 1;
            else 
                group[t]++;
        }
        
        int res = 0;
        for (int i = 1; i <= t; i++){
            res += Math.min(group[i-1], group[i]);
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n) - n is the length of string
* Space Complexity: O(n) - n is the length of string

## Solution - Without storing group
```java
class Solution {
    public int countBinarySubstrings(String s) {
        int prev = 0, curr = 1, res = 0;
      
        for (int i = 1; i < s.length(); i++){
            if (s.charAt(i) != s.charAt(i-1)){
                res += Math.min(prev, curr);
                prev = curr;
                curr = 1;
            }
            else{
                curr++;
            }
        }
        return res += Math.min(prev, curr);
    }
}
```
#### Complexity
* Time Complexity: O(n) - n is the length of string
* Space Complexity: O(1)
