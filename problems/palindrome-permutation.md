# Palindrome Permutation - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/articles/palindrome-permutation/)

Given a string, determine if a permutation of the string could form a palindrome.

Example 1:

Input: "code"

Output: false

# Solution - Brute Force
If a string with an even length is a palindrome, every character in the string must always occur an even number of times. If the string with an odd length is a palindrome, every character except one of the characters must always occur an even number of times.
```java
public class Solution {
    public boolean canPermutePalindrome(String s) {
        int count = 0;
        for (char i = 0; i < 128 && count <= 1; i++) {  // iterate over 128 characters 
            int ct = 0;
            for (int j = 0; j < s.length(); j++) {
                if (s.charAt(j) == i)
                    ct++;
            }
            count += ct % 2;
        }
        return count <= 1;
    }
}
```
## Complexity
* Time Complexity: O(128*n) - n is the length of string
* Space Complexity: O(1)

# Solution - HashMap
Store all elements to HashMap, then traverse the map to see if odd number of count occurs more than once.

```java
public class Solution {
    public boolean canPermutePalindrome(String s) {
        HashMap < Character, Integer > map = new HashMap < > ();
        for (int i = 0; i < s.length(); i++) {
            map.put(s.charAt(i), map.getOrDefault(s.charAt(i), 0) + 1);
        }
        int count = 0;
        for (char key: map.keySet()) {
            count += map.get(key) % 2;
        }
        return count <= 1;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

# Solution - using Array
Traverse through the string, if the char's count is odd, count++, if the char's count is even, count--
```java
public class Solution {
    public boolean canPermutePalindrome(String s) {
        int[] map = new int[128];
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            map[s.charAt(i)]++;
            if (map[s.charAt(i)] % 2 == 0)
                count--;
            else
                count++;
        }
        return count <= 1;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(128)

# Solution - using Set
add element, if the element already exists (even count), remove this element.
```java
public class Solution {
    public boolean canPermutePalindrome(String s) {
        Set < Character > set = new HashSet < > ();
        for (int i = 0; i < s.length(); i++) {
            if (!set.add(s.charAt(i)))
                set.remove(s.charAt(i));
        }
        return set.size() <= 1;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(n) - if all chars are distinct

# Note
* if all characters are letters? ascii (0,127)?
