# Reverse Integer - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-integer/description/)

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123

Output: 321

# Solution - using StringBuilder (Accepted)
```java
class Solution {
    public int reverse(int x) {
        if (x % 10 == x) return x;
        
        StringBuilder str = new StringBuilder();
        str.append(x+"");
        int i = 0, j = str.length()-1;
        while (i < j){
            if (i == 0 && str.charAt(0) == '-'){
                i += 1;
                continue;
            }
            char tmp = str.charAt(i);
            str.setCharAt(i,str.charAt(j));
            str.setCharAt(j,tmp);
            i++;
            j--;
        }
        // need to consider overflow and underflow
        if (Long.parseLong(str.toString()) > Integer.MAX_VALUE || Long.parseLong(str.toString()) < Integer.MIN_VALUE) 
            return 0;
        return Integer.parseInt(str.toString());
    }
}
```
## Complexity
Time Complexity: O(n)

# Solution - optimized
```java
public int reverse(int x){
    int result = 0;

    while (x != 0)
    {
        int tail = x % 10;
        int newResult = result * 10 + tail;
        // because: Integer.MAX_VALUE + positive number a= Integer.MIN_VALUE + positive number (a - 1)
        if ((newResult - tail) / 10 != result) 
            return 0;
        result = newResult;
        x = x / 10;
    }
    return result;
}
```

#Note
* need to consider scientific notation? e?
* float?
* must assume input x is in range [−2^31,  2^31 − 1]