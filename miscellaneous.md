# Miscellaneous

## 1. Private Methods

**\_\_somefunction** - underscore means, in most other languages like Java, when you create a class you can have a private properties that you cannot access outside the class. With Javascript, that is not possible. So there is a common standard which is to put underscore and in JS world, this says that it is a private property that should not be accessed outside the scope.

## 2. The Garbage Collector

Our computers are going to delete the memory that is unused and because it sees that there is still a variable referencing this location in memory and this value in memory, it's not going to delete it \(there is pointer to this location in memory\). How things get deleted in JS is simply removed the pointer and in JS, memory is managed automatically, the memory will get deleted.

## 3. Everything is Object in JS \(Number too\)

```javascript
var a = new Number(5);
typeof a; //Object
var b = 5;
typeof b; //Primitive value: number

a === b; //false
a == b; //true because of type coercion

b.toString(); 
//How is it possible with primitive value to have methods?
```

in JavaScript, when we assign variable, internally it's going to construct the Number object so that we have access to all these methods and that's how we can use things like to fixed or to string. Technically in JavaScript everything is an object with constructor function and methods, except for null and undefined

## 4. Returning Object Literals

```javascript
var func = () => { foo: 1 };
// Calling func() returns undefined!

var func = () => ({ foo: 1 });
// Calling func() returns { foo:1 }
```

## 5. Update Project Dependencies

```javascript
3 Ways:

A. npm audit fix OR npm audit fix --force
(with --force, it may have breaking changes)

B. npm update 
(will look into ^ or >=. If ^, will only update the minor release)

C. change the package.json to the desired version & run npm install
```

## 6. Default Argument

Default arguments only provide default values for `undefined` arguments. Other "falsy" values such as `''`, `""`, `false`, `null`, `0`, and `NaN`, will not be replaced by a default value.

