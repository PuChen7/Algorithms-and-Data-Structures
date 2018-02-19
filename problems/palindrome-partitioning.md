# Palindrome Partitioning - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindrome-partitioning/description/)

Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

For example, given s = "aab",
Return

[
  ["aa","b"],
  ["a","a","b"]
]

## My Solution
```java
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> list = new ArrayList();
        backtrack(list, new ArrayList(), s, 0);
        return list;
    }
    
    private void backtrack(List<List<String>> list, List<String> tempList, String s, int start){
        if (start == s.length()){list.add(new ArrayList(tempList));}
        
        for (int i = start; i < s.length(); i++){
            if (isPalindrome(s, start, i)){
                tempList.add(s.substring(start, i+1));
                backtrack(list, tempList, s, i+1);
                tempList.remove(tempList.size()-1);
            }
        }
    }
    
    private boolean isPalindrome(String s, int lo, int hi){
        while (lo < hi){
            if (s.charAt(lo++) != s.charAt(hi--)) {return false;}
        }
        return true;
    }
}
```

### Backtracking problems
See other backtrack problems:

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Combination Sum III](combination-sum3.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Combination](combination.md)