# Linked List Cycle II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/linked-list-cycle-ii/description/)

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

## My Solution - Version I
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) return null;
        
        ListNode fast = head;
        ListNode slow = head;
        boolean hasCycle = false;
        while (slow != null && fast != null){
            slow = slow.next;
            if (fast.next == null) return null;
            fast = fast.next.next;
            if (fast == slow){
                hasCycle = true;
                break;
            }
        }
        if (!hasCycle) return null;
        ListNode tmp = head;
        while (tmp != slow){
            tmp = tmp.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

Time Complexity: O(n)
