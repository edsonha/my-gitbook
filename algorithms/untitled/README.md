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

{% hint style="success" %}
Anything you can do with recursively can be done iteratively \(loop\)
{% endhint %}

Pros of recursion:

1. More readable
2. DRY principal

Cons of recursion:

1. Not memory efficient

The rule of thumb of when to use recursion is when you're working with data structures that you're not really sure how deep they are or where you don't know how many loops to go through. For example doing traversal in tree data structure.

{% hint style="info" %}
Consider recursion every time you are using a tree or converting something into a tree.

1. Divided into a number of sub-problems that are smaller instances of the same problem 

2. Each instance of the sub-problems is identical in nature

3. The solutions of each sub-problems can be combined to solve the problem at hand

Divide and conquer approach using recursion
{% endhint %}

