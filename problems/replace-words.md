# Replace Words - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/replace-words/)

## Description
 In English, we have a concept called root, which can be followed by some other words to form another longer word - let's call this word successor. For example, the root an, followed by other, which can form another word another.

Now, given a dictionary consisting of many roots and a sentence. You need to replace all the successor in the sentence with the root forming it. If a successor has many roots can form it, replace it with the root with the shortest length.

You need to output the sentence after the replacement.

Example 1:

Input: dict = ["cat", "bat", "rat"]

sentence = "the cattle was rattled by the battery"

Output: "the cat was rat by the bat"

## Thinking & Notes
* Brute Force: Iterate over words, for every word, check each root, if word contains root as prefix.
* HashSet: similar to brute force. using set can eliminate duplicates and I can use `set.contains()` to check.
* Trie: when facing prefix, I should think of `Trie`. First, put all roots into trie. then iterate over sentence, check each char, if prefix found, break.

## Solution - Brute Force
```java
class Solution {
    public String replaceWords(List<String> dict, String sentence) {
        String[] words = sentence.split(" ");
        for (int i = 0; i < words.length; i++){
            String tempRes = null;
            for (String root : dict){
                if (words[i].length() >= root.length() && words[i].substring(0, root.length()).equals(root)){
                    if (tempRes == null) tempRes = root;
                    else if (tempRes.length() > root.length()) tempRes = root;
                }
            }
            //replace
            if (tempRes != null)
                words[i] = tempRes;
        }
        StringBuilder res = new StringBuilder();
        for (int i = 0; i < words.length; i++){
            res.append(words[i]);
            if (i+1 != words.length) res.append(" ");
        }
        return res.toString();
    }
}
```
### Complexity
* Time: O(NM) - (N: length of sentence, M: number of roots)

## Solution - Using HashSet
```java
class Solution {
    public String replaceWords(List<String> dict, String sentence) {
        HashSet<String> set = new HashSet<>();
        for (String item : dict) set.add(item);
        
        StringBuilder res = new StringBuilder();
        
        String[] words = sentence.split(" ");
        for(String w : words){
            String prefix = null;
            for (int i = 1; i <= w.length(); i++){
                prefix = w.substring(0, i);
                if (set.contains(prefix)) break;
            }
            if (res.length() > 0) res.append(" ");
            res.append(prefix);
        }
        return res.toString();
    }
}
```
### Complexity
* Time: O(n^2) (n is the length of word in sentence)
* Space: O(n)

## Solution - Trie
```java
class Solution {
    public String replaceWords(List<String> dict, String sentence) {
        TrieNode trie = new TrieNode();
        for (String root : dict){
            TrieNode curr = trie;
            for (char c : root.toCharArray()){
                if (curr.children[c-'a'] == null)
                    curr.children[c-'a'] = new TrieNode();
                curr = curr.children[c-'a']; 
            }
            curr.word = root; 
        }
        
        StringBuilder res = new StringBuilder();
        for (String w : sentence.split(" ")){
            TrieNode curr = trie;
            if (res.length() > 0) res.append(" ");
            for (char c : w.toCharArray()){
                if (curr.children[c-'a'] == null || curr.word != null) break;
                curr = curr.children[c-'a'];
            }
            res.append(curr.word != null ? curr.word : w);
        }
        return res.toString();
    }
}

class TrieNode{
    String word;
    TrieNode[] children;
    TrieNode(){
        children = new TrieNode[26];
    }
}
```
### Complexity
* Time: O(n)
* Space: O(n)

### Core Algorithm & Data Sructure
* Can do this without data structure. Iterate over string -- brute force
* Can improve a little by using `HashSet`.
* `Trie` is the best solution. Can do it in linear time.
