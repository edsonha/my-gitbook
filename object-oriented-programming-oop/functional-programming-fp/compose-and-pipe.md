# Compose and Pipe

Composition is the idea that any sort of data transformation that we do should be obvious. Compose does not exist in JS, so we have to use outside library like Ramda.

It's kind of like a conveyor belt right in a factory. It's easy to move pieces around to get the desired output based on the user's specific requirements.

```javascript
// Compose function that do two things: 
// multiply by three and make abosulte value.

const compose = (f, g) => data => f(g(data)); // our own created compose function

const multiplyBy3 = num => num * 3;
const returnAbsoluteNumber = num => Math.abs(num);
const multiplyBy3AndAbsolute = compose(
  multiplyBy3,
  returnAbsoluteNumber 
);

console.log(multiplyBy3AndAbsolute(-50));
```

Pipe is similar to compose, but different flow.

```javascript
fn1(fn2(fn3(50))); 
//Create compose and pipe:

compose(fn1, fn2, fn3)(50); //Right to left
//same as
pipe(fn3, fn2, fn1)(50); //left to right

const compose = (f, g) => data => f(g(data));
const pipe = (f, g) => data => g(f(data)); 
```

Compose and pipe function that can take many arguments

```javascript
const compose = (...fns) => fns.reduce((f, g) => (...args) => f(g(...args)));

const pipe = (...fns) => fns.reduceRight((f, g) => (...args) => f(g(...args)));

//Example
const compose = (...fns) => fns.reduce((f, g) => (...args) => f(g(...args)));

const multiplyBy3 = num => num * 3;
const returnAbsoluteNumber = num => Math.abs(num);
const showTwoDecimalPlace = num =>
  parseFloat(Math.round(num * 100) / 100).toFixed(2);
const myFunction = compose(
  showTwoDecimalPlace,
  returnAbsoluteNumber ,
  multiplyBy3
);

console.log(myFunction(-50)); // 150.00
```

With compose and pipe, we've created our little assembly line where we can compose different functions together and they can be assembled in various combinations, these tiny little functions can be easily tested, they are pure functions and at the same time, we're able to compose them together to do something more complex.

