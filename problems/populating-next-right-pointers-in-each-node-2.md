# Populating Next Right Pointers in Each Node II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/description/)

Given a binary tree
```c
struct TreeLinkNode {
  TreeLinkNode *left;
  TreeLinkNode *right;
  TreeLinkNode *next;
}
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

# Solution
```java
/**
 * Definition for binary tree with next pointer.
 * public class TreeLinkNode {
 *     int val;
 *     TreeLinkNode left, right, next;
 *     TreeLinkNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void connect(TreeLinkNode root) {
        TreeLinkNode curr = root;   // current head
        TreeLinkNode head = null;   // the root of next level
        TreeLinkNode prev = null;   // the root of next
        while (curr != null){
            while (curr != null){
                if (curr.left != null){
                    if (prev != null)
                        prev.next = curr.left; // assign the next pointer
                    else
                        head = curr.left;
                    prev = curr.left;
                }

                if (curr.right != null){
                    if (prev != null)
                        prev.next = curr.right;
                    else
                        head = curr.right;
                    prev = curr.right;
                }
                curr = curr.next;
            }
            curr = head;
            prev = null;
            head = null;
        }
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)