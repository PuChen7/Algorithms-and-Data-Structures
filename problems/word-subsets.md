# Word Subsets - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/word-subsets/)

## Description
We are given two arrays A and B of words.  Each word is a string of lowercase letters.

Now, say that word b is a subset of word a if every letter in b occurs in a, including multiplicity.  For example, "wrr" is a subset of "warrior", but is not a subset of "world".

Now say a word a from A is universal if for every b in B, b is a subset of a. 

Return a list of all universal words in A.  You can return the words in any order.

## Thinking & Notes
* Reduce B to single word

## Solution - Reduce B to single word
```java
class Solution {
    public List<String> wordSubsets(String[] A, String[] B) {
        // we can form B into one single word (for every two b, count the most frequent letters)
        // so the problem reduced to how to find if word a contains all letters from b
        int[] bmax = new int[26];
        for (String b : B){
            int[] countb = count(b);
            for (int i = 0; i < countb.length; i++){
                bmax[i] = Math.max(bmax[i], countb[i]);
            }
        }
        
        // now we have count of single word 'b' for each char
        // then we check if word 'a' has at least same count of letters
        List<String> res = new ArrayList<>();
        outer: for (String a : A){
            int[] counta = count(a);
            for (int i = 0; i < counta.length; i++){
                if (counta[i] < bmax[i]) continue outer;
            }
            res.add(a);
        }
        return res;
    }
    
    private int[] count(String s){
        int[] count = new int[26];
        for (char c : s.toCharArray()) count[c - 'a']++;
        return count;
    }
}
```
#### Complexity
* Time Complexity: O(A+B)
* Space Complexity: O(A.length + B.length)

