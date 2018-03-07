# Merge Two Sorted Lists - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/merge-two-sorted-lists/description/)

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4

Output: 1->1->2->3->4->4

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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null && l2 == null)
            return null;
        ListNode h1 = l1;
        ListNode h2 = l2;
        ListNode res = null;
        ListNode curr = null;
        while (h1 != null && h2 != null){
            ListNode tmp = new ListNode(0);
            if (h1.val <= h2.val){
                tmp.val = h1.val;
                h1 = h1.next;
            }else{
                tmp.val = h2.val;
                h2 = h2.next;
            }
            if (res == null){
                res = tmp;
            }else{
                curr.next = tmp;
            }
            curr = tmp;
        }
        if (res == null){
            if (h1 != null) return h1;
            else return h2;
        }
        if (h1 != null && res != null){
            curr.next = h1;
        }else if (h2 != null && res != null){
            curr.next = h2;
        }
        return res;
    }
}
```

## Complexity
Time Complexity: O(n)