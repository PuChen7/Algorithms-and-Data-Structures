
# N-Repeated Element in Size 2N Array - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/n-repeated-element-in-size-2n-array/)

## Description
In a array A of size 2N, there are N+1 unique elements, and exactly one of these elements is repeated N times.

Return the element repeated N times.

Example 1:

Input: [1,2,3,3]

Output: 3

## Thinking & Notes
* HashMap: count occurrence, if a number has `N` occurrence, return.
* Possibility: Pick two numbers at random. You have 1/4 chance of finding the answer. Repeat for great success. O(1) average. 
Notice: except the answer, other numbers are unique. Only need to check with neighbors(1,2,3 distance).

## Solution - HashMap
```java
class Solution {
    public int repeatedNTimes(int[] A) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int num : A){
            if (!map.containsKey(num)) map.put(num, 1);
            else if (map.containsKey(num) && map.get(num)+1 == A.length/2) return num;
            else map.put(num, map.get(num)+1);
        }
        return 0;
    }
}
```
### Complexity
* Time: O(n)
* Space: O(n)

## Solution - Possibility
```java
class Solution {
    public int repeatedNTimes(int[] A) {
        for (int i = 1; i <= 3; i++){
            for (int j = 0; j < A.length - i; j++)
                if (A[j] == A[j+i]) return A[j];            
        }
        return -1;
    }
}
```
### Complexity
* Time: O(n)
* Space: O(1)
