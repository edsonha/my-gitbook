# Currying

It is a technique of translating the evaluation of a function that takes multiple arguments into evaluating a sequence of functions - each with a single argument.

```javascript
const regularMultiply = (a, b) => a * b;

const curriedMultiply = a => b => a * b;
curriedMultiply(5)(20); // 100

const multiplyBy5 = curriedMultiply(5);
multiplyBy5(20); // 100
```

