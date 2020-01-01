# Idempotent

Idempotent - a function that for the same input gives the same output and can have side effects to outside function world. VS pure function - a function that for the same input gives the same output without any side effects. So, idempotent without side effect = pure function. The idea of impotence is a function that always returns or does what we expected to do \(predictable\). It is used in API - given a set of parameter, it will always return the same value, although it is not pure and communicating with the outside world.

```javascript
function notIdempotent(num) {
  return Math.random(num);
}

function goodIdempotent(num) {
  console.log(num);
}
```

