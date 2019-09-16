# Groups of Special-Equivalent Strings - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/groups-of-special-equivalent-strings/)

## Description
You are given an array A of strings.

Two strings S and T are special-equivalent if after any number of moves, S == T.

A move consists of choosing two indices i and j with i % 2 == j % 2, and swapping S[i] with S[j].

Now, a group of special-equivalent strings from A is a non-empty subset S of A such that any string not in S is not special-equivalent with any string in S.

Return the number of groups of special-equivalent strings from A.

## Thinking & Notes
* Counting: for this case, the count of letters of two strings at `odd` and `even` position should be equal. 

## Solution - Counting
```java
class Solution {
    public int numSpecialEquivGroups(String[] A) {
        Set<String> set = new HashSet<>();
        for (String s : A){
            int[] odd = new int[26];
            int[] even = new int[26];
            for (int i = 0; i < s.length(); i++){
                if (i % 2 == 1) odd[s.charAt(i) - 'a']++;
                else even[s.charAt(i) - 'a']++;
            }
            set.add(Arrays.toString(odd) + Arrays.toString(even));
        }
        return set.size();
    }
}
```
#### Complexity
* Time Complexity: O(n*m) - n is the number of strings, m is the length of each string
* Space Complexity: O(n*52) - n is the number of strings
