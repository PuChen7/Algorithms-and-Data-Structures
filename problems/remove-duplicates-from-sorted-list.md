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

The head of the list will not be deleted since the second duplicate will be deleted.
No need to check if the curr is head or not.

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null)
            return head;
        ListNode curr = head;
        while (curr != null){
            if (curr.next == null) break;
            if (curr.val == curr.next.val){
                curr.next = curr.next.next;
            }else{
                curr = curr.next;   
            }
        }
        return head;
    }
}
```

## My Solution - Improved Version III (Using recursion by @wen587sort on leetcode)
```java
public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)return head;
        head.next = deleteDuplicates(head.next);
        return head.val == head.next.val ? head.next : head;
}
```


## Complexity
Time Complexity: O(n)