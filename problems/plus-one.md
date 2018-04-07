# Plus One - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/plus-one/description/)

Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.

## My Solution - Version I
```java
class Solution {
    public int[] plusOne(int[] digits) {
        if (digits == null) return digits;
        
        int n = digits.length;
        for (int i = n-1; i >= 0; i--){
            if (digits[i] < 9){
                digits[i] += 1;
                return digits;
            }
            digits[i] = 0;
        }
        int[] res = new int[n+1];
        res[0] = 1;
        return res;
    }
}
```

Time Complexity: O(n)
