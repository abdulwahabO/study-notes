## Linear Data strucures

### Arrays

An array is a collection of similar data grouped together for fast access. Each array element is assigned a numerical value called an _index_. The first element is at index **0** and the last is at **size - 1**.
Indexing makes direct access to array elements possible. This makes retrieval very fast (`(O(1)` running time).

Arrays have to be initialized with a fixed size which cannot be altered. The only way to add more data to a full array is to create a new, larger array and copy the elements of the old one. This is a costly operation. In memory, array elements are stored as a contiguous stream of data.

### Singly Linked List

A linked list is formed by nodes linked together. In a singly-linked list, each node holds data and a pointer to the next node(except the last node). A singly-linked list supports efficient implementations of stacks and queues. Push/queue and pop/dequeue operations will run in constant time (`O(1)`) because they involve adding or removing the elements at the head or tail. However search and/or deletion of values that are not head or tail runs in linear time (`O(n)`, because there would be list traversal to find the value.

In a doubly-linked list each node has two pointers: one to the previous node, another to the next node. 

_TODO: find out what advantages a DLL has over an SLL. Circular DLL?_


### Stacks and Queues

A stack is a LIFO data structure. All stack operations run in constant time (`O(1)`). A Queue is a FIFO data structure. In a priority queue, elements are sorted based on some ordering.

_TODO: More about stacks and queues_

## Non-Linear data structures

### Graphs






