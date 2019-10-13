# Linked List

Linked list \(Single Linked List\) contains a set of nodes. Each nodes has two elements: value of the data \(any data type\) and a pointer to the next node in line. The first node is called the head and the last node is called the tail. Finally, linked lists are what we call null terminated \(pointer to null\) which signifies that it's the end of the list.

* prepend - add to the beginning of the list O\(1\)
* append - add to the last of the list O\(1\)
* lookup - traversal because we have to go from the head to the node we want to find O\(n\)
* insert - traversal O\(n\)
* delete -  traversal O\(n\)

Pointer is simply a reference to another place in memory or another object or another node

```
let obj1 = {a: true};
let obj2 = obj1
```

What is the difference between linked list and arrays?

1. Linked list has a sort of loose structure that allows you to insert a value into the middle of the list by simply resetting a few pointers and the changes not happen to part of the linked list. The same goes for deleting a node in linked list. VS array, where we have to shift indexes when inserting or deleting
2. 
