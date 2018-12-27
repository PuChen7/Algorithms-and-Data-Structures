# Number Of Boomerangs - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/number-of-boomerangs/)

Given n points in the plane that are all pairwise distinct, a "boomerang" is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Find the number of boomerangs. You may assume that n will be at most 500 and coordinates of points are all in the range [-10000, 10000] (inclusive).

Example:

Input:

[[0,0],[1,0],[2,0]]

Output:
2

Explanation:

The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]]

## Solution
```java
class Solution {
    public int numberOfBoomerangs(int[][] points) {
        if (points == null) return 0;
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        int res = 0;
        for (int i = 0; i < points.length; i++){
            for (int j = 0; j < points.length; j++){
                if (i == j) continue;
                int d = getDistance(points[i], points[j]);
                map.put(d, map.getOrDefault(d, 0)+1);
            }
            
            // permutation
            for (int val : map.values())
                res += val * (val-1);
            map.clear();
        }
        return res;
    }
    
    private int getDistance(int[] p1, int[] p2){
        int x = p1[0] - p2[0];
        int y = p1[1] - p2[1];

        return x*x + y*y;
    }
}
```
