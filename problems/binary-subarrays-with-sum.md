# Binary Subarrays With Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-subarrays-with-sum/)

## Description
In an array A of 0s and 1s, how many non-empty subarrays have sum S?

Example 1:

Input: A = [1,0,1,0,1], S = 2

Output: 4

Explanation: 
The 4 subarrays are bolded below:
[1,0,1,0,1], 
[1,0,1,0,1], 
[1,0,1,0,1], 
[1,0,1,0,1]

## Thinking & Notes
* Brute Force: caculate sum for every sub-array combinations. if sum == S, res++
* Prefix sum + HashMap: 
In this problem we are required to find some interval [i:j] ,i < j where sum[i:j] = target. We know that sum[i:j] = A[i] + A[i+1] +... + A[j].
Let's define prefixSum[j] = A[0] + A[1] + ... + A[j] 0 <= j <= n-1 (n = A.length)
It is easy to see that,
sum[i:j] = A[i] + A[i+1] ... + A[j] =
(A[0] + A[1] + ... A[i] ... + A[j]) - (A[0] + A[1] + ... A[i-1]) =
prefix[j] - prefix[i-1].

Now we the problem reduces to finding # of pairs (i, j) (i < j) such that
prefix[j] - prefix[i-1] = target
This becomes prefix[i-1] = prefix[j] - target with some algebra.
 
## Solution - Brute Force
```java
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        int res = 0;
        for (int i = 0; i < A.length; i++){
            int sum = 0;
            for (int j = i; j < A.length; j++){
                sum += A[j];
                if (sum == S) res++;
            }
        }
        return res;
    }
}
```
### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(1)

## Solution - Prefix sum + HashMap
```java
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int sum = 0;
        int total = 0;
        
        for (int i = 0; i < A.length; i++){
            sum += A[i];
            if (map.get(sum-S) != null) 
                total += map.get(sum-S);
            if (sum == S) total++;
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return total;
    }
}
```
### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

### Core Algorithm & Data Sructure
* Prefix sum
