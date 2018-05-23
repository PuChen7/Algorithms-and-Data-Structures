# Sort Characters By Frequency - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/sort-characters-by-frequency/description/)

Given a string, sort it in decreasing order based on the frequency of characters.

# Solution
```java
class Solution {
    public String frequencySort(String s) {
        if (s == null) return null;
        
        Map<Character, Integer> map = new HashMap<>();
        int max = 0;
        char[] arr = s.toCharArray();
        for (Character c : arr){
            if (!map.containsKey(c))
                map.put(c,0);
            map.put(c, map.get(c)+1);
            max = Math.max(max, map.get(c));
        }
        List<Character>[] list = getList(max, map);
        return getString(list);
    }
    
    public List<Character>[] getList(int max, Map<Character, Integer> map){
        List<Character>[] list = new List[max+1];
        for (Character c : map.keySet()){
            if (list[map.get(c)] == null)
                list[map.get(c)] = new ArrayList();
            list[map.get(c)].add(c);
        }
        return list;
    }
    
    public String getString(List<Character>[] list){
        StringBuilder str = new StringBuilder();
        for (int i = list.length-1; i > 0; i--){
            List<Character> tmp = list[i];
            if (tmp != null){
                for (Character c : tmp)
                    for (int j = 0; j < i; j++) // append i times
                        str.append(c);
            }
        }
        return str.toString();
    }
}
```