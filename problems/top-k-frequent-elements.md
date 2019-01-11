# Top K Frequent Elements - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/top-k-frequent-elements/)

## Description
Given a non-empty array of integers, return the k most frequent elements.

Example 1:

Input: nums = [1,1,1,2,2,3], k = 2

Output: [1,2]

## Thinking & Notes
* Using `HashMap`? I count `occurrences`, but the map is still not sorted. What to do to make map sorted or 
ouput each key in an order? I can `sort` HashMap by `values`, then I can get `K-th` most freq value. 
Then iterate through map for `k` times and add `key` if `value` >= `K-th` most freq value.

* 
## Solution
```java - Using HashMap and Sort Values
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        List<Integer> res = new ArrayList<>();
        HashMap<Integer,Integer> map = new HashMap<>();
        
        for (int item : nums) map.put(item, map.getOrDefault(item, 0)+1);
        
        List<Integer> list = new ArrayList<>(map.values());
        Collections.sort(list, (a,b) -> Integer.compare(b,a));
        int kthFreq = list.get(k-1);
        
        int count = 0;
        for(Integer key: map.keySet()){
            if(map.get(key) >= kthFreq && count < k){
                res.add(key);
                count++;
            }
        }
        return res;
    }
}
```

## Complexity

### Core Algorithm & Data Sructure

### More About this Algorithm & Data Structure?

### Any related or similar problems?
