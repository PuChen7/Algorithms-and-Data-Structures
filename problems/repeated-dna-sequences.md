# Repeated DNA Sequences - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/repeated-dna-sequences/)

## Description
All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.

Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.

Example:

Input: s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"

Output: ["AAAAACCCCC", "CCCCCAAAAA"]

## Thinking & Notes
* Using HashSet: easy to implement. applying `sliding window` technique because we only want string with length 10. 
Keep adding to set, if failed, then we have a duplicate. Need to check if result list contains current substring to prevent adding duplicates.
* Two HashSet: use two sets to prevent adding duplicates. 

## Solution - HashSet
```java
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        if (s.length() < 10 || s == null) return new ArrayList<>();
        List<String> res = new ArrayList<>();
        HashSet<String> set = new HashSet<>();
        
        int start = 0, end = 9;
        
        while (end <= s.length()-1){
            if(!set.add(s.substring(start, end+1)) && !res.contains(s.substring(start, end+1)))
                res.add(s.substring(start, end+1));
            start++;
            end++;
        }
        return res;
    }
}
```
### Complexity
* Time: O(n)

## Solution - Two HashSets
```java
public List<String> findRepeatedDnaSequences(String s) {
    Set seen = new HashSet(), repeated = new HashSet();
    for (int i = 0; i + 9 < s.length(); i++) {
        String ten = s.substring(i, i + 10);
        if (!seen.add(ten))
            repeated.add(ten);
    }
    return new ArrayList(repeated);
}
```

### Core Algorithm & Data Sructure
* The key is `sliding window`, then use two sets to check if set contains the same substring.
