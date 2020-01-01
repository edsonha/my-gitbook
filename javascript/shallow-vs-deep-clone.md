# Shallow vs Deep Clone

In general, when we copy things and whenever we make changes, we expect the original thing to stay the same, whereas the copy changes.

**Copy Primitive Data Types**

When you make a copy, it will be a real copy

```
const a = 5
let b = a
b = 6
console.log(b) // 6
console.log(a) // 5
```

**Copy Objects**

When we assign variable to an object, it just creates a pointer \(reference\) to that value. So if make a copy b = a, changes in "b" will also impact "a" as well since "a" and "b" actually point to the same thing.

```
let obj = {one: 1, two: 2};
let obj2 = obj;
console.log(
  obj,  // {one: 1, two: 2};
  obj2  // {one: 1, two: 2};
)

obj2.three = 3;
console.log(obj); // {one: 1, two: 2, three: 3}; <-- 😱
console.log(obj2); // {one: 1, two: 2, three: 3}; <-- ✅
```

So, there are three ways to copy an object:

```
1. Spread Operator
let obj = {one: 1, two: 2};
let obj2 = {...obj};

obj2.three = 3;
console.log(obj); // {one: 1, two: 2}; <-- ✅
console.log(obj2); // {one: 1, two: 2, three: 3}; <-- ✅

2. Object Assign
let obj = {one: 1, two: 2};
let obj2 = Object.assign({}, obj);

obj2.three = 3;
console.log(obj); // {one: 1, two: 2}; <-- ✅
console.log(obj2); // {one: 1, two: 2, three: 3}; <-- ✅

3. JSON
let obj = {one: 1, two: 2};
let obj2 = JSON.parse(JSON.stringify(obj))

obj2.three = 3;
console.log(obj); // {one: 1, two: 2}; <-- ✅
console.log(obj2); // {one: 1, two: 2, three: 3}; <-- ✅
```

**Shallow Clone vs Deep Clone of Nested Object**

A deep clone means that all of the values of the new variable are copied and disconnected from the original variable, for example, JSON. A shallow clone means that certain \(sub-\)values are still connected to the original variable, for example, spread operator.

```
const nestedObject = {
  country: '🇨🇦',
  city: {
    town: 'vancouver'
  }
};

const shallowClone = { ...nestedObject };
// Changed our cloned object
shallowClone.country = '🇹🇼'
shallowClone.city.town = 'taipei';

console.log(nestedObject); 
// {country: '🇨🇦', city: {town: 'taipei'}} <-- 😱
console.log(shallowClone);
// {country: '🇹🇼', city: {town: 'taipei'}} <-- ✅
```

When you have a nested object \(or array\) and you copy it, nested objects inside that object will not be copied, since they are only pointers / references. In summary, a shallow copy means the first level is copied, deeper levels are referenced. The deep clone is a true copy for nested objects.

```
const deepClone = JSON.parse(JSON.stringify(nestedObject))
// Changed our cloned object
deepClone.country = '🇹🇼'
deepClone.city.town = 'taipei';

console.log(nestedObject);
// {country: '🇨🇦', city: {town: 'vancouver'}} <-- ✅
console.log(deepClone);
// {country: '🇹🇼', city: {town: 'taipei'}} <-- ✅
```

**Copy Arrays**

Copying arrays is just as common as copying objects. A lot of the logic behind it is similar, since arrays are also just objects under the hood.

```
Example 1:
const a = [1,2,3]
let b = [...a]
b[1] = 4
console.log(b[1]) // 4
console.log(a[1]) // 2

Example 2:
Array functions — map, filter, reduce
These methods will return a new array with all (or some) 
values of the original one.
const a = [1,2,3]
const b = a.map((el, index) => index === 1 ? 4 : el)
console.log(b[1]) // 4
console.log(a[1]) // 2

Example 3: 
Similar to objects, using the methods above to copy an array 
with another array or object inside will generate a shallow 
copy. To prevent that, also use JSON
const nestedArray = [
  '🇨🇦', ['vancouver']
];
const shallowClone = [ ...nestedArray ];
// Changed our cloned object
shallowClone[0] = '🇹🇼'
shallowClone[1][0] = 'taipei';

console.log(nestedArray);
// [ '🇨🇦', [ 'taipei' ] ] <-- 😱
console.log(shallowClone);
// [ '🇹🇼', [ 'taipei' ] ] <-- ✅

const deepClone = JSON.parse(JSON.stringify(nestedArray))
// Changed our cloned object
deepClone[0] = '🇹🇼'
deepClone[1][0] = 'taipei';

console.log(nestedArray);
// [ '🇨🇦', [ 'vancouver' ] ] <-- ✅
console.log(deepClone);
// [ '🇹🇼', [ 'taipei' ] ] <-- ✅
```

