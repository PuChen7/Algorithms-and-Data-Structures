# Intersection of Two Linked Lists - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:

A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3

begin to intersect at node c1.


Notes:

If the two linked lists have no intersection at all, return null.

The linked lists must retain their original structure after the function returns.

You may assume there are no cycles anywhere in the entire linked structure.

Your code should preferably run in O(n) time and use only O(1) memory.

## Solution - Version I
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null)
            return null;
        ListNode la = headA;
        ListNode lb = headB;
        while (la != null || lb != null){
            if (la == null){
                la = headB;
                continue;
            }else if (lb == null){
                lb = headA;
                continue;
            }
            if (la == lb) return la;
            la = la.next;
            lb = lb.next;
        }
        return null;
    }
}
```

## Solution - Version II (by @hpplayer on leetcode)
```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null) return null;
        
        ListNode a = headA;
        ListNode b = headB;

        // if no intersection, loop will end when a == b == null
        while( a != b){
            a = a == null? headB : a.next;
            b = b == null? headA : b.next;    
        }
        return a;
    }
}
```

## Complexity
Time Complexity: O(m+n)