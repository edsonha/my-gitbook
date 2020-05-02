# Immutability

Immutability means not changing the data / state, instead we make copies of the state and returning a new state every time a change is made. This is different concept with OOP where we had classes and you can change the name, property of the characters that we are building.

```javascript
const obj = { name: "Andrei" };
function clone(obj) {
  return { ...obj };
}

obj.name = "Andrei"
obj.name = "Nana" //mutate the state

//Ideally you should do this
function updateName(obj) {
  const obj2 = clone(obj);
  obj2.name = "Nana";
  return obj2;
}

const updatedObj = updateName(obj);
console.log(obj, updatedObj); // {name: Andrei}, {name: Nana}
//Now we maintain immutability of not changing the state. 
//Just returning copies or new things every time a change is made.
```

The idea of immutability is very important. We can change things inside of our function, but we don't want it to affect the outside world in our programs.

**Is it memory inefficient to have immutability?**

There's something called structural sharing. The idea behind it is that when a new object or any sort of data structure is created, we don't actually copy everything. Underneath the hood, what happen is that only the changes that were made to the state will be copied. But the things that don't change in memory are actually still there. This combined with the fact that in this day, memory is fairly cheap. It makes sense for some cases and functional programming where we have immutability

