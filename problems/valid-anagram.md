# Valid Anagram - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-anagram/description/)

Given two strings s and t , write a function to determine if t is an anagram of s.

Example 1:

Input: s = "anagram", t = "nagaram"

Output: true

# Solution - sorting
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    char[] str1 = s.toCharArray();
    char[] str2 = t.toCharArray();
    Arrays.sort(str1);
    Arrays.sort(str2);
    return Arrays.equals(str1, str2);
}
```
## Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(1)

# Solution - Hash
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        
        int[] arr = new int[26];
        for (int i = 0; i < s.length(); i++){
            arr[s.charAt(i)-'a']++;
            arr[t.charAt(i)-'a']--;
        }
        for (int i = 0; i < arr.length; i++)
            if (arr[i] != 0) return false;
        return true;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(1) - no matter how large string is, table remain constant