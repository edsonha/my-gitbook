# High Order Function and Closure

In JavaScript, functions are first class citizens which means we can have high order functions - takes one or more functions as arguments or returns a function as a result, often called a callback. And as result, we can also have closures.

**High Order Function**

```
const hof = () => () => 5;
hof()(); // 5

const hof = fn => fn(5);
const a = num => num;
hof(a) // 5
```

**Closure** 

**I**n JS, it is a mechanism for containing the states of variables. We create a closure whenever a function accesses a variable defined outside of the immediate function scope and that is the scope of the parent. Because of closure, this increment function below remembers the variable used by or declared in the outer scope, so the variable used by the inner function will be available to it, even after the outer function has finished running. With closure, we just created private variables / data privacy which is the count

```
const closure = function() {
  let count = 0;
  return function increment() {
    count++;
    return count;
  };
};

const incrementFn = closure();
incrementFn(); //1
incrementFn(); //2
incrementFn(); //3
```

