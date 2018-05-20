# Add Two Numbers - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/add-two-numbers/description/)

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)

Output: 7 -> 0 -> 8

Explanation: 342 + 465 = 807.

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        // check edge case
        if (l1 == null && l2 == null)
            return null;
        
        ListNode dummy = new ListNode(0);
        ListNode list1 =l1, list2 = l2, curr = dummy;
        int carry = 0;
        
        while (list1 != null || list2 != null){
            // if list1 not null, get the value
            int x = 0;
            if (list1 != null)
                x = list1.val;
            // if list2 not null, get the value
            int y = 0;
            if (list2 != null)
                y = list2.val;
            
            int sum = x + y + carry;    // get sum
            carry = sum / 10;   // recalculate carry
            curr.next = new ListNode(sum%10);   // assign digit in tens place
            curr = curr.next;
            
            // increment two lists
            if (list1 != null) list1 = list1.next;
            if (list2 != null) list2 = list2.next;
        }
        
        // if carry not zero, need a new node to hold the digit
        if (carry != 0){
            curr.next = new ListNode(carry);
        }
        return dummy.next;
    }
}
```

Time Complexity: O(max(m,n))
