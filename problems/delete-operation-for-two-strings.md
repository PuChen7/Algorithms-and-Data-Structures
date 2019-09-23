# Delete Operation for Two Strings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/delete-operation-for-two-strings/)

## Description
Given two words word1 and word2, find the minimum number of steps required to make word1 and word2 the same, where in each step you can delete one character in either string.

## Thinking & Notes
* Longest Common SubString
* Longest Common SubString - Dynamic Programming
  * same idea, but without using recursion. The key is to fill up 2-d array to find the longest common sub.
  * the reason why `int[][] path = new int[word1.length()+1][word2.length()+1];` the `length + 1` is because we need to compare all chars, the first char cannot use the same array cell. see detail at Solution in leetcode.

## Solution - Longest Common SubString
```java
class Solution {
    public int minDistance(String word1, String word2) {
        // 2-d array to keep track?
        // res = w1.length + w2.length - (2*longest common sub)
        // problem reduced to how to get longest common sub
        int[][] path = new int[word1.length() + 1][word2.length() + 1]; // use 2-d array to keep longest length
        int m = word1.length(), n = word2.length(); // use m and n to start from last char
        return word1.length() + word2.length() - (2 * longestCommonSub(word1, word2, path, m, n));
        
    }
    
    private int longestCommonSub(String s1, String s2, int[][] path, int m, int n){
        if (m == 0 || n == 0) return 0;
        if (path[m][n] > 0) return path[m][n];  // why we can directly return at here? because the substring is checked already, no need to check multiple times, this saves some time
        if (s1.charAt(m - 1) == s2.charAt(n - 1))   // minus one because length passed in didn't minus 1
            path[m][n] = 1 + longestCommonSub(s1, s2, path, m - 1, n - 1);   // keep going to next char, always save previous res at current position
        else 
            path[m][n] = Math.max(longestCommonSub(s1, s2, path, m - 1, n), longestCommonSub(s1, s2, path, m, n - 1));
        return path[m][n];
    }
}
```
#### Complexity
* Time Complexity: O(m*n)
* Space Complexity: O(m*n)

## Solution - Longest Common SubString - Dynamic Programming
```java
class Solution {
    public int minDistance(String word1, String word2) {
        int[][] path = new int[word1.length()+1][word2.length()+1];
        for (int i = 0; i <= word1.length(); i++){
            for (int j = 0; j <= word2.length(); j++){
                if (i == 0 || j == 0) continue; 
                if (word1.charAt(i-1) == word2.charAt(j-1))
                    path[i][j] = 1 + path[i-1][j-1];
                else
                    path[i][j] = Math.max(path[i-1][j], path[i][j-1]);
            }
        }
        return word1.length() + word2.length() - (2 * path[word1.length()][word2.length()]);
    }
}
```
#### Complexity
* Time Complexity: O(m*n)
* Space Complexity: O(m*n)
