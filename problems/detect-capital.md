# Detect Capital - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/detect-capital/)

## Description
Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:

    All letters in this word are capitals, like "USA".
    All letters in this word are not capitals, like "leetcode".
    Only the first letter in this word is capital, like "Google".

Otherwise, we define that this word doesn't use capitals in a right way. 

## Thinking & Notes
* Three cases: check if three cases are satisfied.
* regex

## Solution - Three cases
```java
class Solution {
    public boolean detectCapitalUse(String word) {
        return word.equals(word.toUpperCase()) ||
            word.equals(word.toLowerCase()) ||
            Character.isUpperCase(word.charAt(0)) && 
            word.substring(1).equals(word.substring(1).toLowerCase());
    }
}
```
#### Complexity
* Time Complexity: O(1)
* Space Complexity: O(1)

## Solution - Regex
```java
public boolean detectCapitalUse(String word) {
    return word.matches("[A-Z]+|[a-z]+|[A-Z][a-z]+");
}
```
#### Complexity
* Time Complexity: O(1)
* Space Complexity: O(1)
