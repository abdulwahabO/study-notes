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

### Graphs

A graph is a set of vertices(nodes) connected by edges. A vertex(_plural_ vertices) is a structure for storing data in a graph. An edge is a pair (x,y) which indicates that vertex x is connected to vertex y. An edge may also show the weight/cost of traversing from x to y. 

In an **undirected raph**, the pair (x,y) implies an edge between x and y where traversal can be from x --> y or vice versa.

In a **directed graph**, the edges are unidirectional. This means for the pair (x,y), traversal can only be from x --> y.

The **degree of a vertex** is the number of edges connected to it. In an undirected graph, and  of a vertex are the same. In a directed graph, **out-degree and in-degree of a vertex** are the numbers of outgoing and incoming edges, respectively. Both values are the same for vertices of an undirected graph.

**Parallel edges** are two or more edges on the same vertices. While a **self loop** is when an edge has the same endpoint as both ends.

#### Representation of a graph

An **adjacency matrix** is a two-dimensional _n x n_ (n = number of vertices) matrix where the rows and columns represent the vertices of a graph, and each cell contains 0 or 1. If a cell contains 1, there is an edge between the corresponding vertices. E.g., _Matrix[a][b] = 1_ means there is an edge between a and b. 

An **adjacency list** is an array of linked lists. The length of the array is the number of vertices in the graph. Each index represents one vertex and contains a linked list of the other vertices to which the index vertex is connected.

It is better to represent a sparse graph with an adjacency list because a matrix would have mostly zeros.

_TODO: Time complexities of add and remove operations on Adjacency matrix and list._

#### Graph Traversal

**Breadth-first search** is a kind of search that grows breadth-wise. I.e., all the vertices at one level are checked before moving down to another level.

**Depth-first search** grows depth-wise. Starting any vertex the search moves through adjacent vertices until the farthest level is reached. 

_TODO: Time complexities of DFS and BFS for both adjacency matrix and list._

### Trees

A tree is a hierarchical data structure of nodes connected by edges/pointers. Trees are similar to graphs except for the fact that cycles cannot exist in a tree.

- **Root Node:** The node at the uppermost level. Has no parent.
- **Parent node:** A node connected to one more nodes at a lower level.
- **Leaf node:** A nod with no child nodes.
- The `depth` of a node is the number of edges from the root to the node. 

A `binary tree` is a type of tree whose nodes which can only have a maximum of two child nodes. A `binary search tree(BST)` is a type of binary tree whose nodes carry comparable data and are ordered so that the data value of a node is greater than the values of it's left subtree and lesser than the values of it's right subtree.

_TODO: Read about insertion, delete and search of BSTs_

_TODO: Read about tries, a data structure useful for working with strings_

### Heaps

Heaps are based on binary trees, and are also commonly known as `Binary Heaps`. For a binary tree to be considered a heap:

* It must be a complete tree: All nodes have max two child nodes except the leaf nodes, and the leaf side of the leaf nodes is never empty. New elements are inserted left to right.
* It must satisfy the heap property. i.e, one of: 
    - Max heap: Values of parent nodes are greater than or equal to those of child nodes.
    - Min heap: Values of parent nodes are less than or equal to those of child nodes.

Heaps are useful for:

- Finding smallest or largest element in an array.
- Priority Queues: These are efficiently implemented using Binary Heaps because `insert` and `delete` run in `O(log N)` time.
- Sorting: HeapSort, a very fast algorithm, uses the heap data structure.

### Hash Tables

A hash table, or hash map or associative array, is a data structure in which keys generated by hashing are mapped to values. This is implemented using arrays. For a given key-value pair, the key is passed through a hash function which calculates the array index at which the value can be found.

If the time complexity of the hash function is ignored, insert, search and delete operations for a hash table operations run in constant time(`O(1)`).

A `hash function` is an algorithm that converts a key to a hash value between 0 - N(where N is the size of the array). A good hash function:
* Is deterministic: Always produces the same value for a given key.
* Provides a uniform distribution of hash values. I.e., every value has an equal probability of been generated.
* Minimises the rate of collisions.

A `collision` occurs when two or more different keys result in the same hash values. This can be remedied by:
* **Linear Probing(or Open Addressing):** This involves checking if the next position in the array is empty. This is not very efficient because the positions closest to the derived index could all be filled and then the algorithm has to keep checking a potentially large array.

**Chaining(or Closed Addressing):** This involves using linked lists as array data instead of the actual values. Every array index maps to a linked list, and any keys that hash to that index have their values stored as nodes in the linked list. The nodes have a field that holds the original(unhashed) key for that value. This way accurate insertion and retrieval is possible even when different keys hash to a given index.

_TODO: Difference between HashMap and HashSet classes in Java_

## References 

- [Open Data Structures](https://opendatastructures.org/ods-python/Contents.html)
