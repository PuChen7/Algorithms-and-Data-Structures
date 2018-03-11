# Remove Nth Node From End of List - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/split-linked-list-in-parts/description/)



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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode curr = head;
        int len = 0;
        while (curr != null){
            curr = curr.next;
            len += 1;
        }
        curr = head;
        int k = len - n;
        ListNode prev = null;
        for (int i = 0; i < k; i++){
            prev = curr;
            curr = curr.next;
        }
        if (curr == head){
            head = head.next;
            return head;
        }
        prev.next = curr.next;
        return head;
    }
}
```

## Complexity
Time Complexity: O(n)