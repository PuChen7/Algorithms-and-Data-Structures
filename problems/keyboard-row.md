# Keyboard Row - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/keyboard-row/)

Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.

## Solution
```java
class Solution {
    public String[] findWords(String[] words) {
        ArrayList<String> res = new ArrayList<String>();
        String[] strs = {"QWERTYUIOP","ASDFGHJKL","ZXCVBNM"};
        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        for (int i = 0; i < strs.length; i++){
            for (char c : strs[i].toCharArray())
                map.put(c, i);
        }
        
        int index;
        for (String w : words){
            index = map.get(w.toUpperCase().charAt(0));
            boolean isOneRow = true;
            for (char c : w.toUpperCase().toCharArray()){
                if (map.get(c) != index){
                    isOneRow = false;
                    break;
                }
            }
            if (isOneRow == true)
                res.add(w);
        }
        return res.toArray(new String[0]);
    }
}
```
