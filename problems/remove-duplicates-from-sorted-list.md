# Remove Duplicates from Sorted List - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,

Given 1->1->2, return 1->2.

Given 1->1->2->3->3, return 1->2->3.

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
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null)
            return head;
        ListNode curr = head;
        while (curr != null){
            if (curr.next == null) break;
            if (curr.val == curr.next.val){
                if (curr == head){
                    head = curr.next;
                    curr = head;
                    continue;
                }else{
                    curr.next = curr.next.next;
                    continue;
                }
            }
            curr = curr.next;
        }
        return head;
    }
}
```

## My Solution - Improved Version II 
```java

```

## Complexity
Time Complexity: O(4^n)

n is the length of the input string.