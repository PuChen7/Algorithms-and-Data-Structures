# Add Strings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/add-strings/)

## Description
Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.

## Thinking & Notes
* Iteration: iterate through both string. Similar to [Add Two Numbers](add-two-numbers.md)

## Solution - Iteration
```java
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder sb = new StringBuilder();
        int sum = 0, carry = 0, i = num1.length()-1, j = num2.length()-1;
        while (i >= 0 || j >= 0 || carry == 1){
            int n1 = i < 0 ? 0 : num1.charAt(i) - '0';
            int n2 = j < 0 ? 0 : num2.charAt(j) - '0';
            sb.append((n1 + n2 + carry) % 10);  // right digit
            carry = (n1 + n2 + carry) / 10;
            i--;
            j--;
        }
        return sb.reverse().toString();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
