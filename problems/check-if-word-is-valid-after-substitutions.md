# Check If Word Is Valid After Substitutions - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/check-if-word-is-valid-after-substitutions/)

## Description
We are given that the string "abc" is valid.

From any valid string V, we may split V into two pieces X and Y such that X + Y (X concatenated with Y) is equal to V.  (X or Y may be empty.)  Then, X + "abc" + Y is also valid.

If for example S = "abc", then examples of valid strings are: "abc", "aabcbc", "abcabc", "abcabcababcc".  Examples of invalid strings are: "abccba", "ab", "cababc", "bac".

Return true if and only if the given string S is valid.

## Thinking & Notes
* Brute force: Using `replace()` to keep replace `abc` with `""`. If the string is valid, then the final string after replace will be empty.

## Solution - Brute force
```java
class Solution {
    public boolean isValid(String S) {
        String abc = "abc";
    	
    	while(S.contains(abc)) {
    		S = S.replace(abc, "");
    	}
        return S.isEmpty();
    }
}
```
#### Complexity
* Time Complexity: O(n^2)
* Space Complexity: O(n^2)?

## Solution - Stack
```java
class Solution {
    public boolean isValid(String S) {
        Stack<Character> stack = new Stack<>();
        for (char c : S.toCharArray()){
            if (c == 'c') {
                if (stack.isEmpty() || stack.pop() != 'b') return false;
                if (stack.isEmpty() || stack.pop() != 'a') return false;
            } else {
                stack.push(c);
            }
        }
        return stack.isEmpty();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
