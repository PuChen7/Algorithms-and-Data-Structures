# Complex Number Multiplication - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/complex-number-multiplication/)

## Description
 Given two strings representing two complex numbers.

You need to return a string representing their multiplication. Note i2 = -1 according to the definition. 

## Thinking & Notes
* Math: think through where each coefficient comes from.
`(a1+b1)*(a2+b2) = (a1a2 + b1b2 + (a1b2+b1a2))`

## Solution - Math
```java
class Solution {
    public String complexNumberMultiply(String a, String b) {
        String[] aSplit = a.split("\\+");
        String[] bSplit = b.split("\\+");
        
        int aBackVal = Integer.parseInt(aSplit[1].substring(0, aSplit[1].length()-1));
        int bBackVal = Integer.parseInt(bSplit[1].substring(0, bSplit[1].length()-1));
        int aFrontVal = Integer.parseInt(aSplit[0]);
        int bFrontVal = Integer.parseInt(bSplit[0]);
        int numOfiSq = aBackVal * bBackVal;
       
        int front = aFrontVal * bFrontVal - numOfiSq;
        int back = aFrontVal * bBackVal + bFrontVal * aBackVal;
        
        return front + "+" + back + "i";
    }
}
```
#### Complexity
* Time Complexity: O(1)
* Space Complexity: O(1)
