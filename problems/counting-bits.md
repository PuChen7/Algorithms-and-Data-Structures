# Counting Bits - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/counting-bits/)

## Description
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

## Thinking & Notes
* Brute force: for every `number`, convert to binary and search for `1`.

## Solution - Brute force
```java
class Solution {
    public int[] countBits(int num) {
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i <= num; i++){
            int count = 0;
            String bi = Integer.toBinaryString(i);
            for (char c : bi.toCharArray()) if (c == '1') count++;
            list.add(count);
        }
        int[] res = new int[list.size()];
        for (int i = 0; i < res.length; i++) res[i] = list.get(i);
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n*size of integer)
* Space Complexity: O(n*size of integer)
