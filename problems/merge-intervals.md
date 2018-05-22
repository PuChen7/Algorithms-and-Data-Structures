# Merge Intervals - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/merge-intervals/description/)

Given a collection of intervals, merge all overlapping intervals.

Example 1:

Input: [[1,3],[2,6],[8,10],[15,18]]

Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].

# Solution
```java
/**
 * Definition for an interval.
 * public class Interval {
 *     int start;
 *     int end;
 *     Interval() { start = 0; end = 0; }
 *     Interval(int s, int e) { start = s; end = e; }
 * }
 */
class Solution {
    // define own compare method
    private class IntervalCompare implements Comparator<Interval>{
        @Override
        public int compare(Interval a, Interval b){
            return a.start < b.start ? -1 : a.start == b.start ? 0 : 1;
        }
    }
    
    public List<Interval> merge(List<Interval> intervals) {
        // sort the list first
        Collections.sort(intervals, new IntervalCompare());
        // use Linked List to store
        LinkedList<Interval> list = new LinkedList<>();
        for (Interval interval : intervals){
            // if list is empty or list last ele end < next interval's start
            if (list.isEmpty() || list.getLast().end < interval.start)
                list.add(interval);
            else    // overlap
                list.getLast().end = Math.max(interval.end, list.getLast().end);
        }
        return list;
    }
}
```
## Complexity
* Time Complexity: O(nlogn) - sorting
* Space Complexity: O(1) for in-place, O(n) for copy
