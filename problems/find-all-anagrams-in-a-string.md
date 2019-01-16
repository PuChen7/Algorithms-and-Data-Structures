# Find All Anagrams in a String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

## Description
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

Example 1:

Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

## Thinking & Notes
* Brute force: check string one by one. for each substring, do sort and compare with sorted target string. if it's a match, put index i into result list.
* Sliding window: 

## Solution
```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        if (s == null) return new ArrayList<>();
        List<Integer> res = new ArrayList<>();
        char[] charArrayP = p.toCharArray();
        Arrays.sort(charArrayP);        
        String sortedP = new String(charArrayP);
        
        for (int i = 0; i < s.length()-p.length()+1; i++){
            String sub = s.substring(i, i+p.length());
            char[] subArr = sub.toCharArray();
            Arrays.sort(subArr);
            String sortedSub = new String(subArr);
            if (sortedP.equals(sortedSub)) res.add(i);
        }
        return res;
    }
}
```
### Complexity
* Time: `O(m*nlogn)`: for each substring, `Arrays.sort()` takes `O(nlogn)`. There are `s.length()-p.length() = m` number of substrings, 
total: `O(m*nlogn)`. Plus a single sort of `p` string: `O(m*nlogn) + O(nlogn) = O(m*nlogn)`.
* Space: O(1)

### Core Algorithm & Data Sructure

### More About this Algorithm & Data Structure?

### Any related or similar problems?
* [Useful link](https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/Sliding-Window-algorithm-template-to-solve-all-the-Leetcode-substring-search-problem.)



