# Queue and Stack

Queue and Stack is similar and the difference is how items get removed from this data structure. Unlike array, there is no random access operation, just commands like push, peak and pop which deal exclusively with element at the beginning or the end of the data structure.

Although it sounds limited, it is important concept in computer science because unlike arrays and linked list, we have less methods or less actions that we can perform on stack and queue and sometimes it's good to have these higher level data structure that are built on top of lower level one like linked list and array to limit the operation you can do on them. 

Having limited ability on data structure is an advantage because you can control whoever is using the data structure to only perform the right operation that are efficient. Rather than give somebody all the tools in the world, it is a lot harder for them to operate that if you just give them two or three so that they know exactly what they need to do.

Stacks - Last In First Out \(LIFO\). Usage: most programming language are modeled with stack architecture and browser history - go back and forward from one website to another.

* Lookup - O\(n\)
* Pop - O\(1\) Pop the last item
* Push - O\(1\) Push to the last item
* Peek - O\(1\) Look at the last item

Queue - First In First Out \(FIFO\). Usage: home printer.

* Lookup - O\(n\)
* Dequeue - O\(1\) Dequeue first person
* Enqueue - O\(1\) Add to the queue
* Peek - O\(1\) Look at the first person

We can build stack and queue using arrays and linked list. With stack, using array and linked list work well and it all depends on what your priorities and preference are. One major thing is with array, it allows something called cache locality which make them technically faster when accessing its items in memory because they are right next each other VS linked list that has them scattered all over memory. Secondly, linked list has extra memory associated as they need to hold value and pointer, but on the other hand, linked list have more dynamic memory \(we can keep adding things to the list\) VS array where it has certain amount of memory and as soon it reach its limit, it is going to double up their memory and create a new space in memory.

With queues, you would prefer using linked list rather than array because it is inefficient to build queue using array. Remember when you dequeue or remove the first person, you have to shift indexes O\(n\) operation VS just resetting the head using linked list O\(1\) operation.

In general, stack and queue have these advantages:

1. Fast operation - for end bits of data structure
2. Fast peek
3. Ordered

The disdavantage is

1. Slow lookup

