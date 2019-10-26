# Partial Application

It is a way for us to partially apply a function. Well, it means taking a function applying some of its arguments into the function, so it remembers those parameters and then it uses closures to later on be called with all the rest of the arguments.

```
const multiply = (a, b, c) => a * b * c;

const partialMultiplyBy5 = multiply.bind(null, 5);
partialMultiplyBy5(10, 2); // 100
partialMultiplyBy5(10); // NaN because the thrid params is undefined

const partialMultiplyBy50 = multiply.bind(null, 5, 10);
partialMultiplyBy50(2); // 100
partialMultiplyBy50(2, 10); //100 as the fourth params is ignored

```

That's the main difference between currying and partial application. Partial application expect all parameter on the second call. VS currying which expect one argument at one time.

