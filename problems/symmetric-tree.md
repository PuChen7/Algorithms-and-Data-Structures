# Symmetric Tree - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/symmetric-tree/description/)

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

# Solution - Recursive
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
    public boolean isSymmetric(TreeNode root) {
        return mirror(root, root);
    }
    
    public boolean mirror(TreeNode r1, TreeNode r2){
        if (r1 == null && r2 == null) return true;
        if (r1 == null || r2 == null) return false;
        return ((r1.val == r2.val) && mirror(r1.right, r2.left) && mirror(r1.left, r2.right));
    }
}
```
## Complexity
Time Complexity: O(n) - n is the number of nodes in the tree

# Solution - Iterative
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
    public boolean isSymmetric(TreeNode root) {
        Queue<TreeNode> q;
        q = new LinkedList<>();
        q.add(root);
        q.add(root);
        while (!q.isEmpty()){
            TreeNode x = q.remove();
            TreeNode y = q.remove();
            if (x == null && y == null) continue;
            if (x == null || y == null) return false;
            if (x.val != y.val) return false;
            q.add(x.left);
            q.add(y.right);
            q.add(x.right);
            q.add(y.left);
        }
        return true;
    }
}
```
## Complexity
* Time COmplexity: O(n)
* Space Complexity: O(n) - using queue