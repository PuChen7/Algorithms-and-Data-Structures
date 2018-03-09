# Palindrome Linked List - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindrome-linked-list/description/)

Given a singly linked list, determine if it is a palindrome.

## My Solution
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
    public boolean isPalindrome(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while (fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;
        }
        if (fast != null)
            slow = slow.next;
        fast = head;
        
        // reverse slow to make it a new head
        ListNode newHead = null;
        while (slow != null){
            ListNode next = slow.next;
            slow.next = newHead;
            newHead = slow;
            slow = next;
        }
        
        while (fast != null && newHead != null){
            if (fast.val != newHead.val)
                return false;
            newHead = newHead.next;
            fast = fast.next;
        }
        return true;
    }
}
```

## Complexity
Time Complexity: O(n+k) = O(n)