# Searching and Traversal

**Searching**

* Linear Search O\(n\)

Linear search is a method of finding a target value within the array using loop. Usually the data is unsorted

* Binary Search O\(log\(n\)\)

If our data is sorted, we can do better than O\(n\) because we essentially mimic the property of binary search trees where we can half the items instead of one at a time when looking for something. That is why storing data in a tree-like data structure is more efficient than a linear data structure like an array.

**Traversal**

Traversals simply means visiting every node and the operation is O\(n\) as we are visiting every single node. So how do we go about doing this in a data structure like a tree or graph? We use Breadth First Search and Depth First Search.

**Breadth First Search** 

O\(n\) time complexity and O\(n\) space complexity where n is the breadth of the tree, because we use queue data structure

We go from root node, then the second level, the third level and so on from left to right. BFS uses additional memory because it is necessary to track every nodes and its child nodes in order on a given level.

Pros: 

* Shortest path - This is more apparent in Graph data structure where it is very good for finding the shortest path between a starting point and any other reachable node because we start off with the root node and then search the closest nodes first and then the node further without taking into account weight of the edges \(the connection\).
* Closer node - If you know that the node is likely in the upper level of a tree, then BFS is better because it will search through the closest node first.

Cons: 

* More memory as we need to keep track of every nodes and its child nodes.

**Depth First Search** 

O\(n\) time complexity and O\(n\) space complexity where n is the height of the tree, because we use stack data structure

The search follows one branch of the tree down as many levels as possible until the target notice found or the end is reached. When the search cannot go on any further, it continues at the nearest ancestor with an unexplored child. DFS has a lower memory requirement than BFS because it's not necessary to store all the nodes and its child nodes.

Pros:

* Less Memory 
* Does path exist? Good at maze solving 

Cons:

* Can get slow if the tree or graph is really deep and it's not necessarily good at finding the shortest path.

**Bellman-Ford and Dijkstra** 

It is algorithm to find the shortest path. 

Pro of Bellman-Ford algorithm can accommodate negative weight VS Dijkstra which cannot do that.

Con of Bellman-Ford algorithm can take a long time to run in term of time complexity with O\(n^2\) on worst case scenario VS Dijkstra which is more efficient.

