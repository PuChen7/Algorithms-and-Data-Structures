# Binary Tree Zigzag Level Order Traversal - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)

Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

# Solution
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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new LinkedList<>();
        traverse(res, root, 0);
        return res;
    }
    
    public void traverse(List<List<Integer>> res, TreeNode root, int level){
        if (root == null) return;
        
        if (res.size() <= level)
            res.add(new LinkedList<>());
        
        List<Integer> tmp = res.get(level);
        if (level % 2 == 0) tmp.add(root.val);
        else tmp.add(0, root.val);
        
        traverse(res, root.left, level+1);
        traverse(res, root.right, level+1);
    }
}
```
## Complexity
* Time Complexity: O(n)