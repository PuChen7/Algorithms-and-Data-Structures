# To Lower Case - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/to-lower-case/)

## Description
Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.

## Thinking & Notes
* ascii: use ascii

## Solution - ascii
```java
class Solution {
    public String toLowerCase(String str) {
        char[] a = str.toCharArray();
        for (int i = 0; i < a.length; i++)
            if ('A' <= a[i] && a[i] <= 'Z')
                a[i] = (char) (a[i] - 'A' + 'a');
        return new String(a);
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

