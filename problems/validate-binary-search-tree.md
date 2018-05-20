# Validate Binary Search Tree - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/validate-binary-search-tree/description/)

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.

The right subtree of a node contains only nodes with keys greater than the node's key.

Both the left and right subtrees must also be binary search trees.

## Solution - In-Order traversal
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
    public boolean isValidBST(TreeNode root) {
        if (root == null) return true;
        
        Stack<TreeNode> stack = new Stack<>();
        TreeNode ptr = null;
        while (root != null || !stack.isEmpty()){
            while (root != null){
                stack.push(root);
                root = root.left;
            }
            root = stack.pop();
            // because this is in-order traversal, so root.val should always >= ptr.val
            if (ptr != null && root.val <= ptr.val) return false;
            ptr = root;
            root = root.right;
        }
        return true;
    }
}
```