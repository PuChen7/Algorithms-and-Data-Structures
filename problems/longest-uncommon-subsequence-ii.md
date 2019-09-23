# Longest Uncommon Subsequence II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-uncommon-subsequence-ii/)

## Description
 Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A subsequence is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be a list of strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1. 

## Thinking & Notes
* Get all subsequences: get all subsequences and store to map. compare each subsequence in map. find the longest one.

## Solution - Get all subsequences
```java
class Solution {
    public int findLUSlength(String[] strs) {
        // the idea is to get all subsequence of each string, 
        // this will get all common and uncommon subsequences 
        // then we need to compare all and find the longest
        Set<String> set = new HashSet<>();
        Map<String,Integer> map = new HashMap<>();
        for (String s : strs){
            for (String sub : getAllSubSeq(s)){
                map.put(sub, map.getOrDefault(sub, 0) + 1);
            }
        }
        int res = -1;
        // compare each one
        for (String key : map.keySet()){
            if (map.get(key) == 1)
                res = Math.max(res, key.length());
        }
        return res;
    }
    
    // get all sub sequences
    private Set<String> getAllSubSeq(String s){
        Set<String> res = new HashSet<>();
        if (s.equals("")){
            res.add("");
            return res;
        }
        Set<String> sub = getAllSubSeq(s.substring(1));
        res.addAll(sub);
        for (String subStr : sub) res.add(s.charAt(0) + subStr);
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(m*n)?
* Space Complexity: O(2 * total number of subseq)?
