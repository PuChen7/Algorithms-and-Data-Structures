# Compare Strings by Frequency of the Smallest Character - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/compare-strings-by-frequency-of-the-smallest-character/)

## Description
Let's define a function f(s) over a non-empty string s, which calculates the frequency of the smallest character in s. For example, if s = "dcce" then f(s) = 2 because the smallest character is "c" and its frequency is 2.

Now, given string arrays queries and words, return an integer array answer, where each answer[i] is the number of words such that f(queries[i]) < f(W), where W is a word in words.

## Thinking & Notes
* Brute force: 
  - for each 'query' in 'queries', compare with each 'word' in 'words'. 
  - Frequency computed by 'function f' will be calculated for each String. 
  - 'Arrays.sort()' will be called many times. Can be improved.
* Binary Search
  - because we need to compare query against all word in words, we can sort words and then do binary search.

## Solution - Brute force
```java
class Solution {
    public int[] numSmallerByFrequency(String[] queries, String[] words) {
        if (words == null || queries == null) return new int[0];
        int[] res = new int[queries.length];
        for (int i = 0; i < queries.length; i++){
            for (int j = 0; j < words.length; j++){
                if (funcF(words[j]) > funcF(queries[i])) res[i]++;
             }
        }
        return res;
    }
    
    private int funcF(String s){
        int count = 1;
        char[] arr = s.toCharArray();
        Arrays.sort(arr);
        for (int i = 1; i < arr.length; i++){
            if (arr[i] != arr[i-1]) break;
            count++;
        }
        return count;
    }
}
```
#### Complexity
* Time Complexity: M*N*NlogN - M is the length of 'queries', N is the length of 'words', NlogN is sorting.
* Space Complexity: O(M)

### Core Algorithm & Data Sructure

### More About this Algorithm & Data Structure?

### Any related or similar problems?
