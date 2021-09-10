# Abstract Data Types 

Abstract Data Types (ADT) provide a convenient way to deal with specific data structures such as 

* Stack
* Queue
* Tree
* [Graph](Graph.md)
* List
* Set
* Dictionary

>MEP Some additional notes
>
>MEP: For the `List` data type are you thinking there might be some built in functions that apply specifically to list data (eg based on LISP?
>
**Graph**
In a graph, data items have associations with one or more other data items in the collection and are somewhat like trees without the concept of a root or a parent-child relationship so that all data items are peers. Examples of operations on graphs are traversals and searches which explore the associations of data items looking for some specific property.  An example is the Spanning tree protocol, which creates a graph (or mesh) representation of a data network and figures out which associations between switching nodes need to be broken to turn it into a tree and thus prevent data going around in loops.

**Tree**
In a tree, which is a special kind of graph, a root data item has associated with it some number of data items which in turn have associated with them some number of other data items in what is frequently viewed as a parent-child relationship. Every data item (other than the root) has a single parent (the root has no parent) and some number of children, possibly zero. Examples of operations on trees are the addition of data items so as to maintain a specific property of the tree to perform sorting, etc. and traversals to visit data items in a specific sequence.
Tree collections can be used to naturally store hierarchical data, which is presented in a tree-like manner, such as menu systems and files in directories on a data storage system.

**Basic Collections**
There are three basic collections
1. A **BAG** is a collection that has no ordering and no restrictions.
2. A **SET** is a collection that has no ordering and does **not** permit repeated objects
3. A **LIST** is a collection where there is an ordering. E.g. an array, a vector and a sequence. T

What about:
stacks;
queues;
priority queues;
double-ended queues;
double-ended priority queues.
