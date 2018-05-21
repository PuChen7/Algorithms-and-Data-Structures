# Copy List with Random Pointer - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/copy-list-with-random-pointer/description/)

A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null.

Return a deep copy of the list.

# Solution
```java
/**
 * Definition for singly-linked list with a random pointer.
 * class RandomListNode {
 *     int label;
 *     RandomListNode next, random;
 *     RandomListNode(int x) { this.label = x; }
 * };
 */
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        // create a duplicate node after itself
        RandomListNode curr = head;
        while (curr != null){
            RandomListNode copy = new RandomListNode(curr.label);
            copy.next = curr.next;
            curr.next = copy;
            curr = copy.next;
        }
        
        // assign random pointer to the duplicate nodes
        curr = head;
        while (curr != null){
            if (curr.random != null){
                curr.next.random = curr.random.next;
            }
            curr = curr.next.next;
        }
        
        // extract the copy and restore the original list
        curr = head;
        RandomListNode dummy = new RandomListNode(0);
        RandomListNode copy = dummy, res = dummy;
        while (curr != null){
            res.next = curr.next;
            res = res.next;
            
            curr.next = curr.next.next;
            curr = curr.next;
        }
        return dummy.next;
    }
}
```

## Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
