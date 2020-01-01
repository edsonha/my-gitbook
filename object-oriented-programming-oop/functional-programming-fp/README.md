# Functional Programming \(FP\)

Functional Programming \(FP\) defines that data \(states\) and behavior \(function\) are distinctly different things and should be kept separate for clarity. So perhaps instead of one giant box to describe everything, like OOP, we have multiple boxes and not combined data and function into one piece or one object. Functions operate on well-defined data structures like arrays and objects, rather than actually belonging to that data structure like object. It is about packaging our codes into separate chunks so that everything is well organized in each part of our code and concern itself with one thing it is good at. FP works really well when it comes to distributed computing where there is multiple machines interacting with data and parallelism where machines working on the same data at the same time.

**Pure Function**

If we break down FP, it all come down to these concept of pure functions. In pure functions, there are two main things:

1. The function cannot modify anything outside itself, meaning no side effect
2. Function always return the same output given the same input

```javascript
// Side effects:
const array = [1, 2, 3]; // global object or shared state
function mutateArray(arr) {
  arr.pop();
}

function mutateArray2(arr) {
  arr.forEach(item => arr.push(1));
}

mutateArray(array); // undefined because not returning anything
array; // [1,2] but array has been modified. This is side effect, the function modify outside of itself, in this case the global object
mutateArray2(array); // the result is this function will get affected because in side effect, the order of the function calls matter.
array; // [1,2,1,1]
```

And that's one of the problems with having side effects is that reusing shared state, like a global variable that can interact with anything and the order of the function calls matter and that can cause a lot of bugs.

```javascript
// Solution to solve side effect using concat and map
const array = [1, 2, 3];
function removeLastItem(arr) {
  const newArray = [].concat(arr); //this is local variable that will get modified, not the outside
  newArray.pop();
  return newArray;
}

function multiplyBy2(arr) {
  return arr.map(item => item * 2); //map create a new array automatically
}

console.log(removeLastItem(array)); //[1,2]
console.log(multiplyBy2(array)); //[2,4,6]
console.log(array); //[1,2,3]
```

```javascript
// not returning the same output for same input
function randomNumber(num) {
  console.log(Math.random(num))
}

// always return the same output for same input
function addition(num1, num2) {
  return num1 + num2;
}
//no side effect as it is not touching outside world, only its own parameter which are local variables
```

**Is it possible to have pure functions?**

As a matter of fact input that return output is a side effect that is communicating with the outside world, so technically it is not pure. Pure functions which are just functions that do something on the inside and the outside world knows nothing about is well, it doesn't do anything because a program cannot exist without side effects.

Thus, the goal of functional programming is not to make everything pure functions, but to minimize side effects. The idea is to organize your code where there is a specific part that has side effects \(isolate them\), but when you have a bug, you know right away to go to that spot because that's where the side effects are happening. As for the rest of your code, since those are just pure functions, we don't have to worry about them as much.

**How to define perfect functions?**

1. One task only =&gt; function should do 1 task only. No massive function 
2. Return statement =&gt; always return output
3. Pure functions 
4. No shared state =&gt; means having no shared state with other functions 
5. Immutable state =&gt; Once something is created, it cannot be changed. We avoid things like shared state. We can modified some of the state within our functions but we always return a new copy of that output. We never just modify our global state 
6. Composable
7. Predictable =&gt; If we understand with 100 percent certainty what our functions do, it makes our code predictable

