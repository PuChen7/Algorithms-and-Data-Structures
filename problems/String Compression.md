# String Compression - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/string-compression/description/)

Given an array of characters, compress it in-place.

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a character (not int) of length 1.

After you are done modifying the input array in-place, return the new length of the array.

# Solution
```java
class Solution {
    public int compress(char[] chars) {
        int write = 0;
        int anchor = 0;
        // (achor, read) this range will be the repeating string
        for (int read = 0; read < chars.length; read++){
            if (read + 1 == chars.length || chars[read] != chars[read+1]){
                chars[write++] = chars[anchor];
                if (read > anchor){ // if repeating, then read must > anchor
                    for (char c : ("" + (read-anchor+1)).toCharArray())
                        chars[write++] = c;
                }
                anchor = read + 1;
            }
        }
        return write;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)