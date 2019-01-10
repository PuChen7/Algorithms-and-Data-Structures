# Word Pattern - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/word-pattern/)

## Description
Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Example 1:

Input: pattern = "abba", str = "dog cat cat dog"
Output: true

## Thinking & Notes


## Solution
```java
class Solution {
    public boolean wordPattern(String pattern, String str) {
        String[] words = str.split(" ");
        if (pattern.length() != words.length) return false;
        Map map = new HashMap();
        for (Integer i = 0; i < words.length; i++){
            if (map.put(words[i], i) != map.put(pattern.charAt(i), i))
                return false;
        }
        return true;
    }
}
```
