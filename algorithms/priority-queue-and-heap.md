# Priority Queue And Heap

## Priority Queue
A PriorityQueue is used when the objects are supposed to be processed based on the priority and follows 
`First-In-First-Out algorithm`. The element with highest priority will be moved to the front of the queue 
and one with lowest priority will move to the back of the queue.

### Example
```java
/* for reverse order
* PriorityQueue<Integer> queue = new PriorityQueue<>(10, Collections.reverseOrder());
*/

// Creating empty priority queue 
PriorityQueue<String> pQueue = new PriorityQueue<String>(); 

// Adding items to the pQueue using add() 
pQueue.add("ABC"); 
pQueue.add("abc"); 
pQueue.add("bda"); 
pQueue.add("234"); 
pQueue.add("678"); 

// Printing all elements 
Iterator itr = pQueue.iterator(); 
while (itr.hasNext()) 
System.out.println(itr.next() + " "); 

/* Output: 234 678 bda abc ABC */
```

## Heap
A heap is a specific `tree` based data structure in which all the nodes of tree are in a `specific order`. 

Mapping the elements of a heap into an array is trivial: if a node is stored a index `k`, then its `left` child is stored
at index `2k+1` and its `right` child at index `2k+2`.


## Heap and Priority Queue
* A priority queue is an abstract datatype. It is a shorthand way of describing a particular interface and behavior, and says nothing about the underlying implementation.

* A heap is a data structure. It is a name for a particular way of storing data that makes certain operations very efficient.

* Heap is an implementation of priority queue,
