# Uncommon Words from Two Sentences - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/uncommon-words-from-two-sentences/)

## Description
We are given two sentences A and B.  (A sentence is a string of space separated words.  Each word consists only of lowercase letters.)

A word is uncommon if it appears exactly once in one of the sentences, and does not appear in the other sentence.

Return a list of all uncommon words. 

You may return the list in any order.

## Thinking & Notes
* Two HashMap: get both string array occurrences. Interate over two map, check condition: map1 has only one occurrence `and` 
 map2 doesn't has this string. 
* One HashMap: No need of two HashMap. Assume combine two string, use one hashmap to store all words, and then extract all words with only one occurrence.

Example 1:

Input: A = "this apple is sweet", B = "this apple is sour"

Output: ["sweet","sour"]

## Solution
```java - Two HashMap
class Solution {
    public String[] uncommonFromSentences(String A, String B) {
        String[] arrA = A.split(" ");
        String[] arrB = B.split(" ");
        
        HashMap<String, Integer> mapA = new HashMap<>();
        HashMap<String, Integer> mapB = new HashMap<>();
        for (String s : arrA) mapA.put(s, mapA.getOrDefault(s, 0)+1);
        for (String s : arrB) mapB.put(s, mapB.getOrDefault(s, 0)+1);
        
        ArrayList<String> res = new ArrayList<String>();

        for (String s : mapA.keySet())
            if (!mapB.containsKey(s) && mapA.get(s) == 1) res.add(s); 
        for (String s : mapB.keySet())
            if (!mapA.containsKey(s) && mapB.get(s) == 1) res.add(s); 
        
        return res.toArray(new String[0]);
    }
}
```
### Complexity
* Time: O(n)
* Space: O(n)

## Solution - One HashMap 
```java
class Solution {
    public String[] uncommonFromSentences(String A, String B) {
        String[] arrA = A.split(" ");
        String[] arrB = B.split(" ");        
        HashMap<String, Integer> mapA = new HashMap<>();
        ArrayList<String> res = new ArrayList<String>();
        
        for (String s : arrA) mapA.put(s, mapA.getOrDefault(s, 0)+1);
        for (String s : arrB) mapA.put(s, mapA.getOrDefault(s, 0)+1);
        
        for (String s : mapA.keySet())
            if (mapA.get(s) == 1) res.add(s);   
        
        return res.toArray(new String[0]);
    }
}
```
### Complexity
* Time: O(n)
* Space: O(n)

### Core Algorithm & Data Sructure
* HashMap
