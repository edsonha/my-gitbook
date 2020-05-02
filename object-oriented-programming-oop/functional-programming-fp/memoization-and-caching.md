# Memoization and Caching

Caching is a way to store values so you can use them later on.

Memoization is a specific form of caching that involves caching the return value of a function based on its parameters.

```javascript
// Without caching
function addTo80(n) {
  console.log("very long calculation");
  return n + 80;
}

addTo80(5);

// With caching - without closure
let cache = {};
function memoizeAddTo80(n) {
  if (n in cache) {// similar to cache.n
    return cache[n];
  } else {
    console.log("very long calculation");
    const answer = n + 80;
    cache[n] = answer;
    return answer;
  }
}

console.log(1, memoizeAddTo80(6));
console.log(cache);
console.log("-----------");
console.log(2, memoizeAddTo80(6));

// With caching and closure
function memoizeAddTo80() {
  let cache = {}; //without return function below, everytime we run, we will get empty cache object
  return function(n) {
    if (n in cache) {
      return cache[n];
    } else {
      console.log("long time");
      const answer = n + 80;
      cache[n] = answer;
      return answer;
    }
  };
}

const memoized = memoizeAddTo80(); // must put this to remember the cache value
console.log(1, memoized(6));
console.log(2, memoized(6));
```

