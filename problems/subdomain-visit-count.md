# Subdomain Visit Count - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/subdomain-visit-count/)

## Description
A website domain like "discuss.leetcode.com" consists of various subdomains. At the top level, we have "com", at the next level, we have "leetcode.com", and at the lowest level, "discuss.leetcode.com". When we visit a domain like "discuss.leetcode.com", we will also visit the parent domains "leetcode.com" and "com" implicitly.

Now, call a "count-paired domain" to be a count (representing the number of visits this domain received), followed by a space, followed by the address. An example of a count-paired domain might be "9001 discuss.leetcode.com".

We are given a list cpdomains of count-paired domains. We would like a list of count-paired domains, (in the same format as the input, and in any order), that explicitly counts the number of visits to each subdomain.

## Thinking & Notes
* HashMap: iterate through domain, for each pair -> store into map and add count.

## Solution - HashMap
```java
class Solution {
    public List<String> subdomainVisits(String[] cpdomains) {
        HashMap<String, Integer> map = new HashMap<>();
        for (String item : cpdomains){
            String[] countDomain = item.split(" ");     
            map.put(countDomain[1], map.getOrDefault(countDomain[1], 0) + Integer.parseInt(countDomain[0]));
            for (int i = 0; i < countDomain[1].length(); i++){
                if (countDomain[1].charAt(i) != '.') continue;
                String sub = countDomain[1].substring(i+1, countDomain[1].length());
                map.put(sub, map.getOrDefault(sub, 0) + Integer.parseInt(countDomain[0]));
            }
        }

        List<String> res = new ArrayList<>();
        for (String key : map.keySet()){
            String singleRes = map.get(key) + " " + key;
            res.add(singleRes);
        }
        
        return res;
    }
}
```

### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
