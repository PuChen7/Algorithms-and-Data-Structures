# Split Array into Fibonacci Sequence - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/split-array-into-fibonacci-sequence/)

## Description
Given a string S of digits, such as S = "123456579", we can split it into a Fibonacci-like sequence [123, 456, 579].

## Thinking & Notes
* Brute Force: start by one char, and compare all left chars one by one.

## Solution - Brute Force
```java
class Solution {
    public List<Integer> splitIntoFibonacci(String S) {
        int N = S.length();
        for (int i = 0; i < Math.min(10, N); i++){
            if (i > 0 && S.charAt(0) == '0') break;
            long a = Long.valueOf(S.substring(0, i+1));
            if (a >= Integer.MAX_VALUE) break;
            
            search: for (int j = i + 1; j < Math.min(i+10, N); j++){
                if (S.charAt(i+1) == '0' && j > i+1) break;
                long b = Long.valueOf(S.substring(i+1, j+1));
                if (b >= Integer.MAX_VALUE) break;
                
                List<Integer> list = new ArrayList<>();
                list.add((int) a);
                list.add((int) b);
                
                int k = j + 1;
                while (k < N){
                    long nextVal = list.get(list.size()-2) + list.get(list.size()-1);
                    if (nextVal <= Integer.MAX_VALUE && S.substring(k).startsWith(String.valueOf(nextVal))){
                        list.add((int) nextVal);
                        k += String.valueOf(nextVal).length();
                    } else 
                        continue search;
                }
                if (list.size() >= 3) return list;
            }
        }
        return new ArrayList<Integer>();
    }
}
```
#### Complexity
* Time Complexity: O(n^3) 
* Space Complexity: O(n)

