# Extra

**Arity** 

The number of arguments a function takes. Although there isn't a solid rule, it usually is a good practice that a fewer number of parameters there are in a function, the easier it is to use that function. Because you can do more interesting things and makes functions more flexible. The more parameters a function has, the harder it is to really compose it with other function. It doesn't mean it's impossible, but it does become a little bit more difficult. Always stick to one or two parameters when it comes to functions.

```javascript
const compose = (f, g) => data => f(g(data)); //arity of 2
const multiplyBy3 = num => num * 3; //arity of 1
```

**Is FP answer to everything?**

It doesn't mean that functional programming is the answer to everything. So, it all depends on the problem you have. There are times when object oriented programming might be better. For example when you are building a fairy tale game and you have clear objects / characters in the game that have some sort of state and methods that can interact with that state, then OOP is the answer. If you have something like an Amazon shopping cart where there's a clear data that needs to get processed, then FP is the answer.

