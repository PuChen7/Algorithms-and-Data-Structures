# Letter Combinations of a Phone Number - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

Given a digit string, return all possible letter combinations that the number could represent.

Input:Digit string "23"

Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

## My Solution
```java
class Solution {
    public List<String> letterCombinations(String digits) {
        LinkedList<String> list = new LinkedList<String>();
        if (digits.length() == 0)
            return list;
        list.add("");
        String[] sample = {"0", "1", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        
        for (int i = 0; i < digits.length(); i++){
            int curr = Character.getNumericValue(digits.charAt(i));
            while (list.peek().length() == i){
                String tmp = list.remove();
                for (char c : sample[curr].toCharArray()){
                    list.add(tmp+c);
                }
            }
        }
        return list;
    }
}
```

## Complexity
Time Complexity: O(4^n)

n is the length of the input string.