# Split Linked List in Parts - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/split-linked-list-in-parts/description/)

Given a (singly) linked list with head node root, write a function to split the linked list into k consecutive linked list "parts".

The length of each part should be as equal as possible: no two parts should have a size differing by more than 1. This may lead to some parts being null.

The parts should be in order of occurrence in the input list, and parts occurring earlier should always have a size greater than or equal parts occurring later.

Return a List of ListNode's representing the linked list parts that are formed.

Examples 1->2->3->4, k = 5 // 5 equal parts [ [1], [2], [3], [4], null ]

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
    public ListNode[] splitListToParts(ListNode root, int k) {
        ListNode cur = root;
        int N = 0;
        while (cur != null) {
            cur = cur.next;
            N++;
        }
        int width = N / k, rem = N % k;
        ListNode[] ans = new ListNode[k];
        cur = root;
        for (int i = 0; i < k; i++) {
            ListNode head = new ListNode(0), write = head;
            for (int j = 0; j < width + (i < rem ? 1 : 0); j++) {
                write = write.next = new ListNode(cur.val);
                if (cur != null) cur = cur.next;
            }
            ans[i] = head.next;
        }
        return ans;
    }
}
```

## Complexity
Time Complexity: O(n+k)

n is the number of nodes in the given list.