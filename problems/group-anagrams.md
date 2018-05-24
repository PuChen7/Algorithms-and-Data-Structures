# Group Anagrams - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/group-anagrams/description/)

Given an array of strings, group anagrams together.

Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

# Solution - sorting
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs.length == 0) return null;
        
        Map<String, List> map = new HashMap<String, List>();
        for (String s : strs){
            char[] ch = s.toCharArray();
            Arrays.sort(ch);
            String key = String.valueOf(ch);
            if (!map.containsKey(key)) map.put(key, new ArrayList());
            map.get(key).add(s);
        }
        return new ArrayList(map.values());
    }
}
```
## Complexity
* Time Complexity: O(N(Klog(K))) - N is the length of strs, K is the length of string in strs
* Space Complexity: O(N*K)

# Solution
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs.length == 0) return null;
        
        Map<String, List> map = new HashMap<String, List>();
        int[] arr = new int[26];
        for (String str : strs){
            Arrays.fill(arr, 0);
            for (int i = 0; i < str.length(); i++)
                arr[str.charAt(i)-'a']++;
            StringBuilder sb = new StringBuilder();
            for (int i = 0; i < 26; i++){
                sb.append(arr[i]);
                sb.append("#");
            }
            String key = sb.toString();
            if (!map.containsKey(key)) map.put(key, new ArrayList());
            map.get(key).add(str);
        }
        return new ArrayList(map.values());
    }
}
```
## Complexity
* Time Complexity: O(N*K)
* Space Complexity: O(N*K)