# Find and Replace Pattern - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-and-replace-pattern/)

## Description
You have a list of words and a pattern, and you want to know which words in words matches the pattern.

A word matches the pattern if there exists a permutation of letters p so that after replacing every letter x in the pattern with p(x), we get the desired word.

Return a list of the words in words that match the given pattern. 

You may return the answer in any order.

## Thinking & Notes
* Two Maps: the first letter of the pattern is `a`, and the first letter of the word is `x`, then in the permutation, `a` must map to `x`.

## Solution - Two Maps
```java
class Solution {
    public List<String> findAndReplacePattern(String[] words, String pattern) {
        Map<Character, Character> wordsMap;
        Map<Character, Character> patMap;
        List<String> res = new ArrayList();
        
        for (String w : words){
            wordsMap = new HashMap<>();
            patMap = new HashMap<>();
            boolean isValid = true;
            for (int i = 0; i < w.length(); i++){
                char wc = w.charAt(i);
                char pc = pattern.charAt(i);
                if (!wordsMap.containsKey(wc)) wordsMap.put(wc, pc);
                if (!patMap.containsKey(pc)) patMap.put(pc, wc);
                if (wordsMap.get(wc) != pc || patMap.get(pc) != wc) isValid = false; 
            }
            if(isValid) res.add(w);
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(N*M)
* Space Complexity: O(N*M)
