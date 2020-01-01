# Examples of Recursion

```javascript
// Factorial
function findFactorialIterative(number) {
  let answer = 1;
  for (let i = 2; i <= number; i++) {
    answer = answer * i;
  }
  return answer;
}

findFactorialIterative(4); //24

function findFactorialRecursive(number) {
  if (number === 0) {
    return 1;
  }
  if (number <= 2) {
    return number;
  }
  return number * findFactorialRecursive(number - 1);
}

findFactorialRecursive(4); //24

// Fibonacci 
// 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144 ...

function fibonacciIterative(n) { //O(n) time complexity
  if (n < 2) {
    return n;
  }
  let array = [0, 1];
  for (let i = 2; i <= n; i++) {
    array.push(array[i - 2] + array[i - 1]);
  }
  return array[n];
}
fibonacciIterative(8); //21

//O(2^N) Exponential time complexity
//Recursive algorithm that solve a problem of size N
function fibonacciRecursive(n) {
  if (n < 2) {
    return n;
  }
  return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

fibonacciRecursive(8); //21
```

```javascript
//Implement a function that reverses a string 
function reverseString(str) { 
    const splitString = str.split(""); 
    let answer = ""; 
    for (let i = splitString.length - 1; i >= 0; i--) { 
        answer = answer + splitString[i]; 
    } 
    return answer; 
}
reverseString("yoyo mastery"); //'yretsam oyoy'

function reverseStringRecursive(str) { 
    if (str === "") { 
        return ""; 
    } else { 
        return reverseStringRecursive(str.substr(1)) + str.charAt(0); 
    } 
}
reverseStringRecursive("yoyo master");
```

