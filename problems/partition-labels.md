# Partition Labels - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/partition-labels/)

## Description
A string S of lowercase letters is given. We want to partition this string into as many parts as possible so that each 
letter appears in at most one part, and return a list of integers representing the size of these parts. 

## Thinking & Notes
* Greedy: store last index of each char into array. If we are at a label that occurs last at some index after j, 
we'll extend the partition j = last[c]. If we are at the end of the partition (i == j) then we'll append a partition 
size to our answer, and set the start of our new partition to i+1.

## Solution - Greedy
```java
class Solution {
    public List<Integer> partitionLabels(String S) {
        List<Integer> res = new ArrayList<>();
        int[] count = new int[26];
        for (int i = 0; i < S.length(); i++)
            count[S.charAt(i)-'a'] = i;
        
        int j = 0, anchor = 0;
        for (int i = 0; i < S.length(); i++){
            j = Math.max(j, count[S.charAt(i)-'a']);
            if (i == j){
                res.add(i - anchor + 1);
                anchor = i + 1;
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
