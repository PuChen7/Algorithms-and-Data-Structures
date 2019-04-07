# Kth Smallest Element in a BST - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

## Description
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

## Thinking & Notes
* Recursion traversal: travrse the tree by go down to the smallest value (left) and decrement count at the same time

## Solution - Recursion traversal - in-order
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
    private static int count;
    private static int res;
    public int kthSmallest(TreeNode root, int k) {
        count = k;
        helper(root);
        return res;
    }
    
    private void helper(TreeNode root) {
        if (root.left != null) helper(root.left);
        count--;
        if (count == 0) {
            res = root.val;
            return;
        }       
        if (root.right != null) helper(root.right);
    }
}
```

### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
