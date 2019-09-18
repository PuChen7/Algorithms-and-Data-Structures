# Find And Replace in String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/find-and-replace-in-string/)

## Description
To some string S, we will perform some replacement operations that replace groups of letters with new ones (not necessarily the same size).

Each replacement operation has 3 parameters: a starting index i, a source word x and a target word y.  The rule is that if x starts at position i in the original string S, then we will replace that occurrence of x with y.  If not, we do nothing.

## Thinking & Notes
* Map and StringBuilder: 
  * store indexes to map as `(indexes[i], i)`, so we have a map, the `key` is the place need to do replace, `value` is used to keep order.
  * iterate `S` with `i`, 
    * if at `i`, map has `i` as key (this place need to replace)
      * StringBuilder append `target` using `value` as order in targets array.
    * if doesn't have key
      * append char in S at `i`

## Solution - Map and StringBuilder
```java
class Solution {
    public String findReplaceString(String S, int[] indexes, String[] sources, String[] targets) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < indexes.length; i++){
            if (S.startsWith(sources[i], indexes[i]))
                map.put(indexes[i], i);
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < S.length();){    // in this for loop, i == map's key (index point that needs to do replace)
            if (map.containsKey(i)){
                sb.append(targets[map.get(i)]);
                i += sources[map.get(i)].length();
            } else {
                sb.append(S.charAt(i));
                i++;
            }
        }
        return sb.toString();
    }
}
```
#### Complexity
* Time Complexity: ? O(N + M * L), where N is the length of S, M is the number of possible replaces, and L is the avg length of each source word.
* Space Complexity: O(n)
