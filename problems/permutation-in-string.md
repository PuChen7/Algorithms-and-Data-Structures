# Permutation in String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/permutation-in-string/)

## Description
Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

Example 1:

Input: `s1 = "ab"`, `s2 = "eidbaooo"`
Output: `True`

Explanation: s2 contains one permutation of s1 ("ba").

## Thinking & Notes
* Sorting: iterate `s2` for `l2-l1` times. for each sub string, sort, then compare.
* Sliding Window: Need to figure out

## Solution - Sorting
```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        s1 = sort(s1);  // sort s1
        for (int i = 0; i <= s2.length() - s1.length(); i++){  // iterate s2 as sliding window
            if (s1.equals(sort(s2.substring(i, i+s1.length())))) return true;
        }
        return false;
    }
    
    public String sort(String s) {
        char[] t = s.toCharArray();
        Arrays.sort(t);
        return new String(t);
    }
}
```
#### Complexity
* Time Complexity: O(l1Log(l1) + (l2-l1)l1Log(l1)) - sort s1 + l2-l1 times substring sort
* Space Complexity: O(l1)

## Solution - Sliding Window
```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int len1 = s1.length(), len2 = s2.length();
        if (len1 > len2) return false;

        int[] count = new int[26];
        for (int i = 0; i < len1; i++) {
            count[s1.charAt(i) - 'a']++;
        }

        for (int i = 0; i < len2; i++) {
            count[s2.charAt(i) - 'a']--;
            if(i - len1 >= 0) count[s2.charAt(i - len1) - 'a']++;
            if (allZero(count)) return true;
        }

        return false;
    }

    private boolean allZero(int[] count) {
        for (int i = 0; i < 26; i++) {
            if (count[i] != 0) return false;
        }
        return true;
    }
}
```
#### Complexity
* Time Complexity: O()
* Space Complexity: O(1)
