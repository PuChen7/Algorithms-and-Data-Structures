# Camelcase Matching - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/camelcase-matching/)

## Description
A query word matches a given pattern if we can insert lowercase letters to the pattern word so that it equals the query. (We may insert each character at any position, and may insert 0 characters.)

Given a list of queries, and a pattern, return an answer list of booleans, where answer[i] is true if and only if queries[i] matches the pattern.

## Thinking & Notes
* Two pointer: use two pointers to keep iterating strings

## Solution - Two pointer
```java
class Solution {
    public List<Boolean> camelMatch(String[] queries, String pattern) {
        char[] pa = pattern.toCharArray();
        List<Boolean> res = new ArrayList<>();
        for (String q : queries){
            res.add(isValid(q, pa));
        }
        return res;
    }
    
    private boolean isValid(String q, char[] pa){
        int j = 0;
        for (int i = 0; i < q.length(); i++){
            if (j < pa.length && q.charAt(i) == pa[j]) j++;
            else if (q.charAt(i) >= 'A' && q.charAt(i) <= 'Z') return false;
        }
        return j == pa.length;
    }
}
```
#### Complexity
* Time Complexity: O(mn)
* Space Complexity: O(1)
