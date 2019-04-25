# Rotate List - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/rotate-list/)

## Description
Given a linked list, rotate the list to the right by k places, where k is non-negative.

## Thinking & Notes
* Circular Linked List: Count the size of the list and move node to tail, then point to the head.
* Two Pointers: no need to make list circular

## Solution - Circular Linked List
```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) return head;
        int size = 1;
        ListNode tail = head;
        while (tail.next != null){   
				size++;  // count size
            tail = tail.next;  // move to tail
        }
        int times = size-k%size;  
        tail.next = head;
        ListNode newTail = head;
        for (int i = 1; i < times; i++){
            newTail = newTail.next;
        }
        head = newTail.next;
        newTail.next = null;
        return head;
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)

## Solution - Two Pointers
```java
public static ListNode rotateRight(ListNode head, int k) {
	if(head==null)
        return null;
	int size = 1; // since we are already at head node
	ListNode fast=head;
	ListNode slow = head;
	
	while(fast.next!=null){
	    size++;
	    fast = fast.next;
	}
	
	for(int i=size-k%size;i>1;i--) // i>1 because we need to put slow.next at the start.
		slow = slow.next;
	
    // No dummy variable.
	fast.next = head;
	head = slow.next;
	slow.next = null;
	
	return head;
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)
