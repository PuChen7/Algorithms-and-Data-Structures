# Reorganize String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reorganize-string/)

## Description
Given a string S, check if the letters can be rearranged so that two characters that are adjacent to each other are not the same.

If possible, output any possible result.  If not possible, return the empty string.

## Thinking & Notes
* Count letters:
  - the key is what pattern will make adjacent letter never touch: `axaxaxax...`
  - fill even first with most frequent letter
  - then fill odd with all other letters
* PriorityQueue
  - the key is using pq to sort char by count in descending order. 
  - poll first highest two, and append to sb
  - if count > 0, count - 1, then add back to queue

## Solution - Count letters
```java
class Solution {
    public String reorganizeString(String S) {
        // the key is what pattern will make adjacent letter never touch: axaxaxax...
        
        // keep counts of all letters
        int[] letterCount = new int[26];
        int mostFreqLetter = 0;
        for (char c : S.toCharArray()){
            letterCount[c - 'a']++;
            if (letterCount[c - 'a'] > letterCount[mostFreqLetter]) mostFreqLetter = c - 'a';
        }
        if (letterCount[mostFreqLetter] > (S.length() + 1) / 2) return ""; // impossible
        char[] res = new char[S.length()];
        // fill in even position
        int i = 0;
        while (letterCount[mostFreqLetter] > 0){
            res[i] = (char) (mostFreqLetter + 'a');
            i += 2;
            letterCount[mostFreqLetter]--;
        }
        
        // fill odd position
        for (int j = 0; j < letterCount.length; j++){
            int count = letterCount[j];
            while (count > 0){
                if (i >= S.length()) i = 1;
                res[i] = (char) (j + 'a');
                count--;
                i += 2;
            }       
        }
        return new String(res);
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(26 + n)

## Solution - PriorityQueue
```java
class Solution {
    public String reorganizeString(String S) {
        int[] countLetter = new int[26];
        for (char c : S.toCharArray()) countLetter[c - 'a']++;
        
        PriorityQueue<Node> pq = new PriorityQueue<>((a,b) -> b.count - a.count);
        for (int i = 0; i < countLetter.length; i++){
            if (countLetter[i] > (S.length() + 1) / 2) return "";
            if (countLetter[i] > 0) pq.add(new Node(countLetter[i], (char) (i + 'a')));
        }
        
        StringBuilder sb = new StringBuilder();
        while (pq.size() >= 2){
            Node n1 = pq.poll();
            Node n2 = pq.poll();
            sb.append(n1.c);
            sb.append(n2.c);
            if (--n1.count > 0) pq.add(n1);
            if (--n2.count > 0) pq.add(n2);
        }
        if (!pq.isEmpty()) sb.append(pq.poll().c);
        return sb.toString();
    }
}

class Node{
    int count;
    char c;
    public Node(int count, char c){
        this.count = count;
        this.c = c;
    }
}
```
#### Complexity
* Time Complexity: O(NlogA)), where N is the length of S, and A is the size of the alphabet. If A is fixed, this complexity is O(N).
* Space Complexity: O(A)

