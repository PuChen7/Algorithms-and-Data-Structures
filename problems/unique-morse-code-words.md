# Unique Morse Code Words - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/unique-morse-code-words/)

## Description
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cba" can be written as "-.-..--...", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.

## Thinking & Notes
* HashSet: HashSet doesn't contains duplicates

## Solution - HashSet
```java
class Solution {
    public int uniqueMorseRepresentations(String[] words) {
        String[] morse = {".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
        Set<String> set = new HashSet<>();
        StringBuilder sb = new StringBuilder();
        for (String w : words){
            for (char c : w.toLowerCase().toCharArray()){
                sb.append(morse[c-'a']);
            }
            set.add(sb.toString());
            sb.setLength(0);
        }
        return set.size();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
