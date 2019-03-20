# Longest Substring Without Repeating Characters - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

## Thinking & Notes
* Sliding Window: use HashSet to store the characters in current window, slide right index to next if no duplicates. until detected duplicates. do this for all **i**.
* HashMap: `Sliding Window` can be optimized by define a mapping of the characters to its index. Then we can skip the characters immediately when we found a repeated character. 

## Solution I - Sliding Window
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int res = 0, i = 0, j = 0;
        Set<Character> set = new HashSet<>();
        while (i < n && j < n){
            if (!set.contains(s.charAt(j))) {
                set.add(s.charAt(j++)); // increment j
                res = Math.max(res, set.size());
            } else {
                set.remove(s.charAt(i++));
            }
        }
        return res;
    }
}
```
* Time Complexity: O(2n) -> O(n). Worst case: each char will be visited twice by `i` and `j`
* Space Complexity: O(min(m,n)). The size of the Set is upper bounded by the size of the string n and the size of the charset/alphabet m.

## Solution II - Using HashMap
```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length(), ans = 0;
        Map<Character, Integer> map = new HashMap<>(); 
        for (int j = 0, i = 0; j < n; j++) {
            if (map.containsKey(s.charAt(j))) {
                i = Math.max(map.get(s.charAt(j)), i);
            }
            ans = Math.max(ans, j - i + 1);
            map.put(s.charAt(j), j + 1);
        }
        return ans;
    }
}
```

## Solution III - Using Array with ASCII
```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length(), ans = 0;
        int[] index = new int[128]; // current index of character
        // try to extend the range [i, j]
        for (int j = 0, i = 0; j < n; j++) {
            i = Math.max(index[s.charAt(j)], i);
            ans = Math.max(ans, j - i + 1);
            index[s.charAt(j)] = j + 1;
        }
        return ans;
    }
}
```

### Complexity
* Time Complexity: O(n): iterate j times
* Space Complexity (HashMap): O(min(m,n))
* Space Complexity (Array): O(m): m is the size of charset
