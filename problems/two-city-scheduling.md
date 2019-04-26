# Two City Scheduling - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/two-city-scheduling/)

## Description
There are 2N people a company is planning to interview. The cost of flying the i-th person to city A is costs[i][0], and the cost of flying the i-th person to city B is costs[i][1].

Return the minimum cost to fly every person to a city such that exactly N people arrive in each city.

## Thinking & Notes
* Greedy: We sort the array by the `difference` between costs for A and B. Then, we fly first N people to A, and the rest - to B.
  * Explanation: https://leetcode.com/problems/two-city-scheduling/discuss/278898/Java-2ms-sorting-solution-with-explanation

## Solution - Greedy
```java
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        // sort array by difference btw A,B city
        Arrays.sort(costs, new Comparator<int[]>() {
            public int compare(int[] a, int[] b) {
                return (a[1] - a[0]) - (b[1] - b[0]);
            }
        });
        int cost = 0;
        // first half -> B, second half -> A
        for (int i = 0; i < costs.length / 2; i++) {
            cost += costs[i][1] + costs[costs.length-i-1][0];
        }
        return cost;
    }
}
```
#### Complexity
* Time Complexity: O(nlogn)
* Space Complexity: O(1)
