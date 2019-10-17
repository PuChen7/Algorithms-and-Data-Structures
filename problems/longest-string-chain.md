# Longest String Chain - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-string-chain/)

## Description
Given a list of words, each word consists of English lowercase letters.

Let's say word1 is a predecessor of word2 if and only if we can add exactly one letter anywhere in word1 to make it equal to word2.  For example, "abc" is a predecessor of "abac".

A word chain is a sequence of words [word_1, word_2, ..., word_k] with k >= 1, where word_1 is a predecessor of word_2, word_2 is a predecessor of word_3, and so on.

Return the longest possible length of a word chain with words chosen from the given list of words.

## Thinking & Notes
* DP:
  - sort `words` by each word length. order of each word doesn't matter because we only need length.
  - for each `word`
    - make it missing one char at one time
    - find max length

## Solution - DP
```java
class Solution {
    public int longestStrChain(String[] words) {
        // need to sort words by each word length
        // no need to worry about word order, because we only need length
        Map<String, Integer> dp = new HashMap<>();
        Arrays.sort(words, (a, b)->a.length() - b.length());
        int res = 0;
        for (String w : words){
            int best = 0;
            for (int i = 0; i < w.length(); i++){
                // missing one char 
                String tmp = w.substring(0, i) + w.substring(i+1, w.length());
                // if this missing one char string match with any string before
                best = Math.max(best, dp.getOrDefault(tmp, 0) + 1);
            }
            dp.put(w, best);
            res = Math.max(res, best);
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(NlogNS)
* Space Complexity: O(NS)
