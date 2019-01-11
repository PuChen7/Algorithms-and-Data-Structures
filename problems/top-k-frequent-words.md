# Top K Frequent Words - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/top-k-frequent-words/)

## Description
Given a non-empty list of words, return the k most frequent elements.

Your answer should be sorted by frequency from highest to lowest. If two words have the 
same frequency, then the word with the lower alphabetical order comes first.

## Solution
```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        HashMap<String, Integer> map = new HashMap<>();
        
        for (String w : words) map.put(w, map.getOrDefault(w, 0) + 1);
        
        PriorityQueue<String> heap = new PriorityQueue<>(
            (n1,n2) -> 
            map.get(n1).equals(map.get(n2)) ? n2.compareTo(n1) : map.get(n1)-map.get(n2)
        );
        
        for (String key : map.keySet()){
            heap.add(key);
            if (heap.size() > k)
                heap.poll();
        }
        
        List<String> res = new ArrayList<>();
        while (!heap.isEmpty())
            res.add(heap.poll());
        Collections.reverse(res);
        return res;
    }
}
```

## Complexity
Time Complexity: `O(Nlog⁡k)`
Space Complexity: `O(N)`

### Core Algorithm & Data Sructure
* Using Min-Heap. Similar problem with [Top K Frequent Elements](top-k-frequent-elements.md)
