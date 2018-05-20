# Min Stack - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/min-stack/description/)

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.

## Solution I - using two Stacks
```java
class MinStack {
    Stack<Integer> minStack; // use a regular stack to hold min values
    Stack<Integer> stack;   // use a regular stack to perform basic operations
    /** initialize your data structure here. */
    public MinStack() {
        minStack = new Stack<Integer>();
        stack = new Stack<Integer>();
    }
    
    public void push(int x) {
        stack.push(x);  // push the x into the regular stack
        if (minStack.isEmpty() || x <= minStack.peek()){ // if the minStack is empty, or the new input is smaller
            minStack.push(x);   // then push x to minStack as the new min value
        }
    }
    
    public void pop() {
        // pop regular stack first, then check if it is the min, 
        // if it is, then pop the minStack
        if (stack.pop().equals(minStack.peek())) minStack.pop(); 
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return minStack.peek();
    }
}
```

### Notes
Few things to note:
* is there a top limit for stack?
* negative or float number in stack?
* to compare, use `.equals()`. `if (stack.pop().equals(minStack.peek()))`

### Worst Space Complexity
input in descending order: [4,3,2,1], then two stacks will have the same elements

## Solution II - using Node
```java
class MinStack {
    // define a Node class
    private class Node{
        int val;
        int min;
        Node next;
        private Node(int val, int min, Node next){
            this.val = val;
            this.min = min;
            this.next = next;
        }
    }
    
    private Node head;
    
    public void push(int x) {
        // if the stack is empty, create a new node, set x as the min value
        if (head == null) head = new Node(x, x, null);  
        // if the stack is not empty, create a new node with min(x, head.min) as the min value
        else head = new Node(x, Math.min(x, head.min), head);
    }
    
    public void pop() {
        head = head.next;
    }
    
    public int top() {
        return head.val;
    }
    
    public int getMin() {
        return head.min;
    }
}
```