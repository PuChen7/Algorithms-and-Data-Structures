# H-Index - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/h-index/)

## Description
Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h 
citations each, and the other N − h papers have no more than h citations each."

## Thinking & Notes
* Using counting sort: keep an extra index to store number of citation which is greater than number of paper.

```java
class Solution {
    public int hIndex(int[] citations) {
        int[] index = new int[citations.length+1];
        
        for (int item : citations){
            if (item >= citations.length)
                index[citations.length]++;
            else
                index[item]++;
        }
        
        int res = 0;
        for (int i = citations.length; i > 0; i--){
            res += index[i];
            if (res >= i) return i;
        }
        return 0;
    }
}
```
