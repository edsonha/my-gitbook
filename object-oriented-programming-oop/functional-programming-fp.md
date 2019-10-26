# Functional Programming \(FP\)

Functional Programming \(FP\) defines that data \(states\) and behavior \(function\) are distinctly different things and should be kept separate for clarity. So perhaps instead of one giant box to describe everything, like OOP, we have multiple boxes and not combined data and function into one piece or one object. Functions operate on well-defined data structures like arrays and objects, rather than actually belonging to that data structure like object. It is about packaging our codes into separate chunks so that everything is well organized in each part of our code and concern itself with one thing it is good at. FP works really well when it comes to distributed computing where there is multiple machines interacting with data and parallelism where machines working on the same data at the same time.

Pure Function

If we break down FP, it all come down to these concept of pure functions. In pure functions, there are two main things:

1. Function always return the same output given the same input
2. The function cannot modify anything outside itself, meaning no side effect

```
//Side effects:
const array = [1, 2, 3]; // global object or shared state
function mutateArray(arr) {
  arr.pop();
}

function mutateArray2(arr) {
  arr.forEach(item => arr.push(1));
}

mutateArray(array); //undefined because not returning anything
array; // [1,2] but array has been modified. This is side effect, the function modify outside of itself, in this case the global object
mutateArray2(array); // the result is this function will get affected because in side effect, the order of the function calls matter.
array; // [1,2,1,1]
```

