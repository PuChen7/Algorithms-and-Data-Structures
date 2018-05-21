# Implement Stack using Queues - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/implement-stack-using-queues/description/)

Implement the following operations of a stack using queues.

* push(x) -- Push element x onto stack.
* pop() -- Removes the element on top of the stack.
* top() -- Get the top element.
* empty() -- Return whether the stack is empty.

# Solution - Using two Queues 
```java
class MyStack {
    Queue<Integer> q1, q2;
    int front;
    /** Initialize your data structure here. */
    public MyStack() {
        q1 = new LinkedList<>();
        q2 = new LinkedList<>();
    }
    
    /** Push element x onto stack. */
    public void push(int x) {
        q2.add(x); 
        front = x;
        while (!q1.isEmpty()){
            q2.add(q1.remove());
        }
        Queue<Integer> temp = q1;
        q1 = q2;
        q2 = temp;
    }
    
    /** Removes the element on top of the stack and returns that element. */
    public int pop() {
        int tmp = q1.remove();
        if (!q1.isEmpty()) front = q1.peek();
        return tmp;
    }
    
    /** Get the top element. */
    public int top() {
        return front;
    }
    
    /** Returns whether the stack is empty. */
    public boolean empty() {
        return q1.isEmpty();
    }
}
```

# Solution - Using one Queue
```java
class MyStack {
    Queue<Integer> q1;
    /** Initialize your data structure here. */
    public MyStack() {
        q1 = new LinkedList<>();
    }
    
    /** Push element x onto stack. */
    public void push(int x) {
        q1.add(x);
        int i = q1.size();
        while (i > 1){
            q1.add(q1.remove());
            i--;
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    public int pop() {
        return q1.remove();
    }
    
    /** Get the top element. */
    public int top() {
        return q1.peek();
    }
    
    /** Returns whether the stack is empty. */
    public boolean empty() {
        return q1.isEmpty();
    }
}
```
## Complexity
Time Complexity: O(n) for push()
