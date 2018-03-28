# Reverse Linked List II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/reverse-linked-list-ii/description/)

Reverse a linked list from position m to n. Do it in-place and in one-pass.

For example:

Given 1->2->3->4->5->NULL, m = 2 and n = 4,

return 1->4->3->2->5->NULL.

## My Solution - Version I
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int m, int n) {
        if (head == null || head.next == null) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = dummy;
        for (int i = 1; i < m; i++) prev = prev.next;
        ListNode curr = prev.next;
        ListNode next = curr.next;
        for (int i = 0; i < n-m; i++){
            curr.next = next.next;
            next.next = prev.next;
            prev.next = next;
            next = curr.next;
        }
        return dummy.next;
    }
}
```

## Complexity
Time Complexity: O(n)