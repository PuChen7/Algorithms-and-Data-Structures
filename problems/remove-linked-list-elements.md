# Remove Linked List Elements - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/palindrome-linked-list/description/)

Remove all elements from a linked list of integers that have value val.

Example

Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6

Return: 1 --> 2 --> 3 --> 4 --> 5

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
    public ListNode removeElements(ListNode head, int val) {
        if (head == null)
            return head;
        ListNode curr = head;
        ListNode prev = null;
        
        while (curr != null){
            if (curr.val == val){
                if (curr == head){
                    head = head.next;
                    curr = head;
                }else{
                    prev.next = curr.next;
                    curr = curr.next;
                }
            }else{
                prev = curr;
                curr = curr.next;   
            }
        }
        return head;
    }
}
```

## Complexity
Time Complexity: O(n)