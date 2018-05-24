# Balanced Binary Tree - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/balanced-binary-tree/description/)

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

# Solution - Top Down Approach
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
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        int left = depth(root.left);
        int right = depth(root.right);
        return Math.abs(left-right) <= 1 && isBalanced(root.left) && isBalanced(root.right);
    }
    
    public int depth(TreeNode root){
        if (root == null) return 0;
        return Math.max(depth(root.left), depth(root.right))+1; 
    }
}
```
## Complexity
* Time Complexity: O(n^2)

# Solution - Bottom Up Approach
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
    public boolean isBalanced(TreeNode root) {
        return height(root) != -1;
    }
    
    public int height(TreeNode root){
        if (root == null) return 0;
        int left = height(root.left);
        if (left == -1) return -1;
        int right = height(root.right);
        if (right == -1) return -1;
        if (Math.abs(left-right) > 1) return -1;
        return Math.max(left, right)+1;
    }
}
```
## Complexity
* Time Complexity: O(n)