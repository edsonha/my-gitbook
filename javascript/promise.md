# Promise

Promise All

 The **`Promise.all()`** method takes an iterable of promises as an input, and returns a single [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to an array of the results of the input promises. This returned promise will resolve when all of the input's promises have resolved, or if the input iterable contains no promises. It rejects immediately upon any of the input promises rejecting or non-promises throwing an error, and will reject with this first rejection message / error.

```text
const url = ['www.url1.com', 'www.url2.com', 'www.url3.com']

Promise.all(urls.map(url => {
    return fetch(url).then(resp => resp.json())
})).then(results => {
    console.log(result[0])
    console.log(result[1])
    console.log(result[2])
}).catch(() => console.log('error')

With Async Await

const [users, posts, todos] = await Promise.all(urls.map(url => {
    return fetch(url).then(resp => resp.json())
}))
console.log('users', users)
console.log('posts', posts)
console.log('todos', todos)
```

