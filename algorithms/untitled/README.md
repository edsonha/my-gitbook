# Recursion

Recursion isn't technically an algorithm. It's more of a concept. It is a function that call itself inside of the function. It is really good for tasks that have repeated sub tasks to do.

Two problems of recursion is the risk of stack overflow and it is not memory efficient as our stacks need to hold and remember these function call.

```text
let counter = 0;
function inception() {
  while (counter > 3) {
    return "done";
  }
  counter++;
  return inception(); 
  //Need to have return so that it can bubble up the 'done'. 
  //Without the return, it will return undefined
}

inception();
```

Three things to remember when creating recursive function:

1. Establish Base Case / Stop Point
2. Establish Recursive Case
3. Create two returns for base and recursive case

