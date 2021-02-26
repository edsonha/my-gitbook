# New ES Edition

Optional Chaining Operator

Instead of causing an error if a reference is [nullish](https://developer.mozilla.org/en-US/docs/Glossary/Nullish) \([`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null) or [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined)\), the expression short-circuits with a return value of `undefined`

```text
const adventurer = {
  name: 'Alice',
  cat: {
    name: 'Dinah'
  }
};

const dogName = adventurer.dog?.name;
console.log(dogName); // undefined
console.log(adventurer.dog.name) 
// Uncaught TypeError: Cannot read property 'name' of undefined

```

Nullish Coalescing Operator

 a logical operator that returns its right-hand side operand when its left-hand side operand is [`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null) or [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined), and otherwise returns its left-hand side operand. This can be contrasted with the [logical OR \(`||`\) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR), which returns the right-hand side operand if the left operand is _any_ [falsy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators#description)[ __](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators#description)value, not only `null` or `undefined`.

```text
const foo = null ?? 'default string';
console.log(foo);
// expected output: "default string"

const foo2 = null || 'default string';
console.log(foo2);
// expected output: "default string"

const baz = 0 ?? 42;
console.log(baz);
// expected output: 0

const baz2 = 0 || 42;
console.log(baz2);
// expected output: 42
```

Globalthis

```text
globalThis is the universal that was previously use in browser as (window. ) 
and in terminal as (global. )
```

