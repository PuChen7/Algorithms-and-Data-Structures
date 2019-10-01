# Repeated String Match - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/repeated-string-match/)

## Description
Given two strings A and B, find the minimum number of times A has to be repeated such that B is a substring of it. If no such solution, return -1.

For example, with A = "abcd" and B = "cdabcdab".

Return 3, because by repeating A three times (“abcdabcdabcd”), B is a substring of it; and B is not a substring of A repeated two times ("abcdabcd").

## Thinking & Notes
* StringBuilder: 
  - append A until A.length > B.length. 
  - check if A contains B
    - if not: append one more time `A`, then check. because `A` is already longer than `B`. if appending ome more `A` still doesn't contain `B`, then it's not valid.

## Solution - StringBuilder
```java
class Solution {
    public int repeatedStringMatch(String A, String B) {
        int res = 0;
        StringBuilder sb = new StringBuilder();
        while (sb.length() < B.length()) {
            sb.append(A);
            res++;
        }
        if (sb.toString().contains(B)) return res;
        if (sb.append(A).toString().contains(B)) return res+1;
        return -1;
    }
}
```
#### Complexity
* Time Complexity: O(B) ?
* Space Complexity: O(AB) ?
