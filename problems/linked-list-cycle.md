# Linked List Cycle - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/linked-list-cycle/description/)

Given a linked list, determine if it has a cycle in it.

## My Solution
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
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null)
            return false;
        ListNode walker = head;
        ListNode runner = head.next;
        while (walker != runner){
            if (runner == null || runner.next == null)
                return false;
            walker = walker.next;
            runner = runner.next.next;
        }
        return true;
    }
}
```

## Complexity
n is the length of non-cyclic length

k is cyclic length

Time Complexity: O(n+k) = O(n)