# Construct String from Binary Tree - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/construct-string-from-binary-tree/)

## Description
You need to construct a string consists of parenthesis and integers from a binary tree with the preorder traversing way.

The null node needs to be represented by empty parenthesis pair "()". And you need to omit all the empty parenthesis pairs that don't affect the one-to-one mapping relationship between the string and the original binary tree.

## Thinking & Notes
* Pre-order traversal: to satisfy `one-to-one relationship`, need to add empty `()` when `left == null` and `right != null`

## Solution - Pre-order traversal
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public String tree2str(TreeNode t) {
        if (t == null) return "";
        if (t.left == null && t.right == null) return t.val + "";
        if (t.right == null) return t.val + "(" + tree2str(t.left) + ")";
        return t.val+"("+tree2str(t.left)+")("+tree2str(t.right)+")";
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
