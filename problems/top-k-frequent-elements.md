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

* Using `Bucket Sort`: count frequency using `HashMap`. Create a list array. Map `numbers(key)` into list by `index(freq)`. Iterate through list `backwards` `(freq(index): max -> min)`. check if `res size < k`.

* Using `Min-Heap` (PriorityQueue): Count frequencies and store into `HashMap`. I can use `min-heap` to keep input number sorted `(min->max)`. Iterate through HashMap and keep inserting. When heap reached size `k`, `poll` after `add`, so that heap contains `k` most frequent numbers.

## Solution - Using HashMap and Sort Values
```java
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

## Solution - Using Bucket Sort
```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        List<Integer>[] bucket = new List[nums.length+1];
        HashMap<Integer, Integer> map = new HashMap<>();
        
        // count frequency
        for (int item : nums) map.put(item, map.getOrDefault(item, 0)+1);
        
        // map numbers into bucket array
        for (Integer key : map.keySet()){
            int freq = map.get(key);
            if (bucket[freq] == null)   // if this spot is empty
                bucket[freq] = new ArrayList<Integer>();    // create a new list
            bucket[freq].add(key);  // add key. key is the number, index is freq
        }
        
        List<Integer> res = new ArrayList<>();  // result list
        // iterate through bucket backwards(freq(index): max -> min). check if res size < k.
        for (int i = bucket.length - 1; i >= 0 && res.size() < k; i--){
            if (bucket[i] != null) 
                res.addAll(bucket[i]);
        }
        return res;
    }
}
```
## Complexity
Time Complexity: `O(n)`

## Solution - Using Min-Heap (PriorityQueue)
```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int item : nums) map.put(item, map.getOrDefault(item, 0)+1);
        
        PriorityQueue<Integer> heap = new PriorityQueue<Integer>((n1,n2) -> map.get(n1) - map.get(n2));
        
        for (Integer key : map.keySet()){
            heap.add(key);
            if (heap.size() > k) 
                heap.poll();
        }
        
        List<Integer> res = new ArrayList<>();
        
        while (!heap.isEmpty())
            res.add(heap.poll());
        
        Collections.reverse(res);
        return res;
    }
}
```
### Complexity
Time: `O(nlogk)`: `O(n)` time to get frequency. `O(nlogk)` time to build heap and output.
Space: `O(n)` for HashMap

### Core Algorithm & Data Sructure
* HashMap and Sort Values: Main idea is sort hashmap by `values` in `descending order`. Then iterate through key set by k times.
* Bucket Sort: Main idea is Using Bucket Sort
