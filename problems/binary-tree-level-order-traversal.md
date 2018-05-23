# Binary Tree Level Order Traversal - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

# Solution - using Queue
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new LinkedList<List<Integer>>();
        Queue<TreeNode> q = new LinkedList<>();
        if (root == null) return res;
        
        q.offer(root);
        while (!q.isEmpty()){
            List<Integer> tmp = new LinkedList<>();
            int size = q.size();
            for (int i = 0; i < size; i++){
                if (q.peek().left != null) q.offer(q.peek().left);
                if (q.peek().right != null) q.offer(q.peek().right);
                tmp.add(q.poll().val);
            }
            res.add(tmp);
        }
        return res;
    }
}
```
## Complexity
* Time Complexity: O(n)

# Solution - using pre-order traversal
```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> res = new ArrayList<List<Integer>>();
    levelHelper(res, root, 0);
    return res;
}

public void levelHelper(List<List<Integer>> res, TreeNode root, int height) {
    if (root == null) return;
    if (height >= res.size()) {
        res.add(new LinkedList<Integer>());
    }
    res.get(height).add(root.val);
    levelHelper(res, root.left, height+1);
    levelHelper(res, root.right, height+1);
}
```