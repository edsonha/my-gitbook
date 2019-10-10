# Array

Organize items sequentially.

* lookup O\(1\)  - search item, for example array\[0\]
* append:
* * push O\(1\) - Add at the end of the array:
  * pop O\(1\) - Remove the last item of the array
* insert: 
* * unshift O\(n\) - Insert at the start of the array
* delete:
* * splice O\(n\) - Insert or delete 

There are two types of array:

1. Static array - the length of an array or the size is predetermined, like in Java
2. Dynamic array - the size of an array is not predetermined. If you need to add data, the array will be rebuilt at a new location with more memory. That is why the append can be O\(n\) because it need to loop all over again to rebuild the array



