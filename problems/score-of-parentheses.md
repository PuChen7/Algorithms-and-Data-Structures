# Score of Parentheses - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/score-of-parentheses/)

## Description
Given a balanced parentheses string S, compute the score of the string based on the following rule:
- () has score 1
- AB has score A + B, where A and B are balanced parentheses strings.
- (A) has score 2 * A, where A is a balanced parentheses string.

## Thinking & Notes
- Stack: we can keep score (depth of parentheses. For example, the dot in (()(.())) has depth 2) in a stack. 
`notice: the string of parentheses comes as balanced`. When we see an opening bracket, we increase our depth, 
and our score at the new depth is 0. When we see a closing bracket, we add twice the score of the previous deeper part

- Count layers: The final sum will be a sum of powers of 2, as every core (a substring (), with score 1) 
will have it's score multiplied by 2 for each exterior set of parentheses that contains that core.

  - for bit operator: Take "(()(()))" as an example. Calculation should be 2 * (1 + 2 * 1). If we multiply 2 after finishing calculation of everything in parentheses, that should be a recursion thinking, thus implementing with a stack. But now, if you open up all the parentheses, calculation becomes 2 * 1 + 2 * 2 * 1. Whenever you meet a () pair, you multiply 1 by all the 2 outside of it, and accumulate the result. Therefore, we accumulate res with 2 to the power of layer - 1. The correctness is guaranteed by distributive property. For example, a * (b + c) = a * b + a * c


## Solution - Stack
```java
class Solution {
    public int scoreOfParentheses(String S) {
        Stack<Integer> stack = new Stack<>();
        stack.push(0);  // used as current score
        
        for (char c : S.toCharArray()){
            if (c == '('){
                stack.push(0);
            } else{
                int v = stack.pop();
                int p = stack.pop();
                stack.push(p + Math.max(2 * v, 1));
            }
        }
        return stack.pop();
    }
}
```
#### Complexity
* Time Complexity: O(n) - n is the length of string 
* Space Complexity: O(n) - n is the size of stack

## Solution - Count layers
```java
class Solution {
    public int scoreOfParentheses(String S) {
        int layer = 0, res = 0;
        for (int i = 0; i < S.length(); i++){
            if (S.charAt(i) == '('){
                layer++;
            } else {
                layer--;
                if (S.charAt(i-1) == '('){
                    res += 1 << layer;
                }
            }
        }
        return res;
    }
}
```
#### Complexity
* Time Complexity: O(n) - n is the length of string 
* Space Complexity: O(1)

### Core Algorithm & Data Sructure
* Stack
