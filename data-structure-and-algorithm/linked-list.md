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

What is the difference between linked list and array?

1. Linked list has a sort of loose structure that allows you to insert a value into the middle of the list by simply resetting a few pointers and the changes not happen to part of the linked list. The same goes for deleting a node in linked list. VS array, where we have to shift indexes when inserting or deleting
2. In an array, elements are indexed. So very fast lookup. VS Linked List, where we have to traverse from the head to find the node we want. This idea of traversal is similar to iteration in arrays except for traversal because you don't really know when the linked list will end.

What is the difference between linked list and hash table?

1. The one advantage linked list is there is some sort of order . Each node points to the next node.

What is Double Linked List?

It is similar to Single Linked List except it has links to the node before it \(previous\) and this allows us to traverse our list backwards. So, if we know which half of the list we are looking for, we can pick the optimum place to start. 

Pro of Single Linked List vs Double Linked List

1. Less memory \(as there is no data pointing to previous node\), so with less memory, it is technically faster to do things like insert and delete. VS Double Linked List has higher space complexity as it hold little bit more memory by pointing to the previous node
2. Simpler to implement compared to Double Linked List

Pro of Double Linked List vs Single Linked List

1. Can be traverse form the back VS Single Linked List that can only be done from the front
2. With Single Linked List, as there is no reference to previous Node, if we were to lose the reference, it will be lost in memory. So Single Linked List is appropriate to use when you have less memory
3. Better search operation as you can search backwards instead of just forward

In general, Linked list has these advantages:

1. Fast insertion - compared to array, there is no need to shift index
2. Fast deletion 
3. Ordered - no random insertion
4. Flexible size - Can be added. If we keep adding to items to the array, eventually it will copy the array in memory and double up the space when it reaches the limit to create a larger array

And the disadvantages are:

1. Slow lookup - there's no random access in the sense that when looking for something you have to actually traverse the list
2. More memory - create node which hold value and pointer





