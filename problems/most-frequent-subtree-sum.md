# Most Frequent Subtree Sum - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/most-frequent-subtree-sum/)

## Description
 Given the root of a tree, you are asked to find the most frequent subtree sum. The subtree sum of a node is defined as the sum of all the node values formed by the subtree rooted at that node (including the node itself). So what is the most frequent subtree sum value? If there is a tie, return all the values with the highest frequency in any order.

Examples 1
Input:

  5
 /  \
2   -3

return [2, -3, 4], since all the values happen only once, return all of them in any order. 

## Thinking & Notes
* Post-Order traversal and HashMap: traverse the tree using `post-order` traversal. calculate every sub-tree sum and store into map.
Locate the max count, then get the result.

## Solution - Post-Order traversal and HashMap
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
    HashMap<Integer, Integer> map;
    int max;
    public int[] findFrequentTreeSum(TreeNode root) {
        map = new HashMap<>();
        TreeNode curr = root;
        helper(curr);
        
        List<Integer> list = new ArrayList<>();
        for (int key : map.keySet()){
            if (map.get(key) == max) list.add(key);
        }
        
        int[] res = new int[list.size()];
        for (int i = 0; i < list.size(); i++){
            res[i] = list.get(i);
        }
        
        return res;
    }
    
    private int helper(TreeNode root){
        if (root == null) return 0;
        
        int left = helper(root.left);
        int right = helper(root.right);
        
        int sum = left + right + root.val;
        int count = map.getOrDefault(sum, 0) + 1;
        map.put(sum, count);
        max = Math.max(max, count);
        
        return sum;
    }
}
```

### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)

### Core Algorithm & Data Sructure
* Post-Order Traversal
* HashMap
