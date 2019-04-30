# Most Common Word - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/most-common-word/)

## Description
Given a paragraph and a list of banned words, return the most frequent word that is not in the list of banned words.  It is guaranteed there is at least one word that isn't banned, and that the answer is unique.

Words in the list of banned words are given in lowercase, and free of punctuation.  Words in the paragraph are not case sensitive.  The answer is in lowercase.

## Thinking & Notes
* HashMap & Regex: count occurrences

## Solution - HashMap & Regex
```java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        String[] words = paragraph.toLowerCase().split("[ !?',;.]+");
        List<String> list = Arrays.asList(banned);
        Map<String, Integer> map = new HashMap<>();
        for (String w : words){
            if (list.contains(w)) continue;
            map.put(w, map.getOrDefault(w, 0) + 1);
        }
        String res = null;
        for(String word : map.keySet())
            if(res == null || map.get(word) > map.get(res))
                res = word;
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
