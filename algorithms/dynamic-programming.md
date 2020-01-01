# Dynamic Programming

Dynamic Programming is an optimization technique using caching. At higher level, dynamic programming is a way to solve problems by breaking them down into a collection of sub-problems and solving each of these sub-problems just once and storing their solution for future use. One form of caching is memoization - a way to remember a solution to a solved problem.

We can reduce the time complexity of Fibonacci algorithm by using memorization.

```javascript
//0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233...

let calculations = 0;
function slowFibonacci(n) { //O(2^n), but better space complexity
  // calculations++;
  if (n < 2) {
    return n
  }
  return slowFibonacci(n-1) + slowFibonacci(n-2);
}

function fastFibonacci() { //O(n), but worse space complexity
  let cache = {};
  return function fib(n) {
    calculations++;
    if (n in cache) {
      return cache[n];
    } else {
      if (n < 2) {
        return n;
      } else {
        cache[n] = fib(n-1) + fib(n-2);
        return cache[n];
      }
    }
  }
}

function fibonacciMaster(n) {
  let answer = [0,1];
  for ( let i = 2; i <= n; i++) {
    answer.push(answer[i-2]+ answer[i-1]);
  }
  return answer.pop();
}

const fasterFib = fastFibonacci();

console.log('Slow', slowFibonacci(10))
console.log('DP', fasterFib(100));
console.log('DP2', fibonacciMaster(100));
console.log('we did ' + calculations + ' calculations');
```

Rules of using dynamic programming:

1. Can the problem be divided into sub-problems? Meaning recursive solution
2. Are there repetitive sub-problems? Memoize sub-problems

