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

## My Solution - Improved Version II

* Checking of which list is null is put on the top.
* No need to create node at each iteration. Just make the next equals to the l1 or l2.
* Note to return `res.next`

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
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        ListNode res = new ListNode(0);
        ListNode curr = res;
        while (l1 != null && l2 != null){
            if (l1.val <= l2.val){
                curr.next = l1;
                l1 = l1.next;
            }else{
                curr.next = l2;
                l2 = l2.next;
            }
            curr = curr.next;
        }
        if (l1 != null){
            curr.next = l1;
        }else if (l2 != null){
            curr.next = l2;
        }
        return res.next;    // res is 0 so return the next node
    }
}
```

## My Solution - Version III using recursion (Not recommended for practical use)

this code is actually a stack structured recursive method. Thus it will use extra space, possible risk of stack overflow.

```java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null) return l2;
		if(l2 == null) return l1;
		if(l1.val < l2.val){
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		} else{
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
    }
}
```
## Complexity
Time Complexity: O(n)