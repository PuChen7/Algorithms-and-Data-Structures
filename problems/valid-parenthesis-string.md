# Valid Parenthesis String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-parenthesis-string/)

## Description
 Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

    - Any left parenthesis '(' must have a corresponding right parenthesis ')'.
    - Any right parenthesis ')' must have a corresponding left parenthesis '('.
    - Left parenthesis '(' must go before the corresponding right parenthesis ')'.
    - '*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string.
    - An empty string is also valid.

## Thinking & Notes
* Linear Scan:
  - first, think of different `cases`, for example: `((*)`
    - `*` can be treated as three cases: `(` and `)` and `""`.
    - so in this thinking, we can keep two counts to keep track of two cases.
      - when we see a `*`, we go two ways
        1. `((()`
        2. `(())`
  - low : take '*' as ')', if there are some '(' not matched
  - high : take '*' as '('
  - 
  - if high < 0 means too much ')'
  - if low > 0 , after the count finished, means too much '('

## Solution - Linear Scan
```java
class Solution {
    public boolean checkValidString(String s) {
        int lo = 0, hi = 0;
        for (char c : s.toCharArray()){
            if (c == '('){
                lo++;
                hi++;
            } else if (c == ')'){
                if (lo > 0) lo--;
                hi--;
            } else {    // if *, of lo > 0, means there's at least a (, then take this * as ), so minus 1
                if (lo > 0) lo--;
                hi++;   // always take this as (
            }
            if (hi < 0) return false;   // too many )
        }
        return lo == 0;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
