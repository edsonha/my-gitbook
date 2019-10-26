# High Order Function and Closure

In JavaScript, functions are first class citizens which means we can have high order functions - takes one or more functions as arguments or returns a function as a result, often called a callback. And we can also have closures.

**High Order Function**

```
const hof = () => () => 5;
hof()(); // 5

const hof = fn => fn(5);
hof(function a(x) {
  return x;
});
```

