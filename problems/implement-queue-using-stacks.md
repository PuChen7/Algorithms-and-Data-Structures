# Implement Queue using Stacks - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/implement-queue-using-stacks/description/)

Implement the following operations of a queue using stacks.

* push(x) -- Push element x to the back of queue.
* pop() -- Removes the element from in front of queue.
* peek() -- Get the front element.
* empty() -- Return whether the queue is empty.

# Solution - Using two stacks
```java
class MyQueue {
    // stack1 holds the queue structure, stack2 is used to move elements
    Stack<Integer> stack1, stack2;
    private int front;
    /** Initialize your data structure here. */
    public MyQueue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        if (stack1.isEmpty())
            front = x;
        while (!stack1.isEmpty())
            stack2.push(stack1.pop());
        stack1.push(x);
        while (!stack2.isEmpty())
            stack1.push(stack2.pop());
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        int ele = stack1.pop();
        // update front
        if (!stack1.empty())    
            front = stack1.peek();
        return ele;
    }
    
    /** Get the front element. */
    public int peek() {
        return front;
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        if (stack1.isEmpty()) return true;
        return false;
    }
}
```
### Complexity
* push() - 4n + 2 times for push and pop. O(n)
* pop() - O(1)
* peek() - O(1)
* empty - O(1)

# Solution - Amortized O(1)
```java
class MyQueue {
    // stack1 holds the queue structure, stack2 is used to move elements
    Stack<Integer> stack1, stack2;
    private int front;
    /** Initialize your data structure here. */
    public MyQueue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        if (stack1.isEmpty()) front = x;
        stack1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        if (stack2.isEmpty()){
            while (!stack1.isEmpty()){
                stack2.push(stack1.pop());
            }
        }
        return stack2.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if (!stack2.isEmpty()) return stack2.peek();
        return front;
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return stack1.isEmpty() && stack2.isEmpty();
    }
}
```