# Valid Parenthesis String - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/valid-parenthesis-string/)

## Description
 Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

    - Any left parenthesis '(' must have a corresponding right parenthesis ')'.
    - Any right parenthesis ')' must have a corresponding left parenthesis '('.
    - Left parenthesis '(' must go before the corresponding right parenthesis ')'.
    - '*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string.
    - An empty string is also valid.

## Thinking & Notes
* Linear Scan:
  - first, think of different `cases`, for example: `((*)`
    - `*` can be treated as three cases: `(` and `)` and `""`.
    - so in this thinking, we can keep two counts to keep track of two cases.
      - when we see a `*`, we go two ways
        1. `((()`
        2. `(())`
  - low : take '*' as ')', if there are some '(' not matched
  - high : take '*' as '('
  - 
  - if high < 0 means too much ')'
  - if low > 0 , after the count finished, means too much '('
  
* Backtracking
    - How to check valid parenthesis w/ only ( and )? Easy. Count each char from left to right. When we see (, count++; when we see ) count--; if count < 0, it is invalid () is more than (); At last, count should == 0.
    - This problem added `*`. The easiest way is to try 3 possible ways when we see it. Return true if one of them is valid.

* Stack:
 - The basic idea is to track the index of the left bracket and star position.
Push all the indices of the star and left bracket to their stack respectively.
STEP 1: Once a right bracket comes, pop left bracket stack first if it is not empty. If the left bracket stack is empty, pop the star stack if it is not empty. A false return can be made provided that both stacks are empty.

 - STEP 2: Now attention is paid to the remaining stuff in these two stacks. Note that the left bracket CANNOT appear after the star as there is NO way to balance the bracket. In other words, whenever there is a left bracket index appears after the Last star, a false statement can be made. Otherwise, pop out each from the left bracket and star stack.

 - STEP 3: A correct sequence should have an empty left bracket stack. You don't need to take care of the star stack.

- Final Remarks: Greedy algorithm is used here. We always want to use left brackets to balance the right one first as the * symbol is a wild card. There is probably an O(1) space complexity but I think this is worth mentioning.

## Solution - Linear Scan
```java
class Solution {
    public boolean checkValidString(String s) {
        int lo = 0, hi = 0;
        for (char c : s.toCharArray()){
            if (c == '('){
                lo++;
                hi++;
            } else if (c == ')'){
                if (lo > 0) lo--;
                hi--;
            } else {    // if *, of lo > 0, means there's at least a (, then take this * as ), so minus 1
                if (lo > 0) lo--;
                hi++;   // always take this as (
            }
            if (hi < 0) return false;   // too many )
        }
        return lo == 0;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Backtracking
```java
class Solution {
    public boolean checkValidString(String s) {
        return check(s, 0, 0);
    }
    
    private boolean check(String s, int start, int count){
        if (count < 0) return false;
        for (int i = start; i < s.length(); i++){
            if (s.charAt(i) == '('){
                count++;
            } else if (s.charAt(i) == ')'){
                if (count <= 0) return false;
                count--;
            } else if (s.charAt(i) == '*') {
                // three cases: '(' || "" || ')'
                return check(s, i+1, count+1) || check(s, i + 1, count) || check(s, i + 1, count - 1);
            }
        }
        return count == 0;
    }
}

/************************** Without using for loop *********************************/

class Solution {
    public boolean checkValidString(String s) {
        return check(s, 0, 0);
    }
    
    private boolean check(String s, int start, int count){
        if (start == s.length())
            return count == 0;
        
        if (count < 0) return false;
        if (s.charAt(start) == '('){
            return check(s, start+1, count+1);
        } else if (s.charAt(start) == ')'){
            return check(s, start+1, count-1);
        } else {    // this is a * 
            // three cases: '(' || "" || ')'
            return check(s, start+1, count+1) || check(s, start + 1, count) || check(s, start + 1, count - 1);
        }
    }
}
```
#### Complexity
* Time Complexity: O(3^n)
* Space Complexity: O(1)

## Solution - Stack
```java
class Solution {
    public boolean checkValidString(String s) {
        Stack<Integer> star = new Stack<>();
        Stack<Integer> left = new Stack();
        for (int i = 0; i < s.length(); i++){
            if (s.charAt(i) == '(') left.push(i);
            else if (s.charAt(i) == '*') star.push(i);
            else {
                if (star.isEmpty() && left.isEmpty()) return false;
                else if (!left.isEmpty()) left.pop();
                else star.pop();
            }
        }
        
        while (!star.isEmpty() && !left.isEmpty())
            if (left.pop() > star.pop()) return false;
        return left.isEmpty();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(m+k) - two stacks
