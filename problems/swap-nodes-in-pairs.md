# Swap Nodes in Pairs - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

## Solution - Version I
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
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null)
            return head;
        ListNode curr = head;
        ListNode next = head.next;
        ListNode prev = null;
        while (curr != null && next != null){
            curr.next = next.next;
            next.next = curr;
            if (prev != null){
                prev.next = next;
            }
            if (curr == head){
                head = next;
            }
            prev = curr;
            curr = curr.next;
            if (curr != null)
                next = curr.next;
        }
        return head;
    }
}
```

## Solution - Version II (using extra head to avoid edge case)
```java
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode curr = dummy;
        
        while (curr.next != null && curr.next.next != null){
            ListNode first = curr.next;
            ListNode second = curr.next.next;
            first.next = second.next;
            curr.next = second;
            second.next = first;
            curr = first;
        }
        return dummy.next;
    }
}
```

## Complexity
Time Complexity: O(n)