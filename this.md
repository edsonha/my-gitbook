# This

```
// Four types of binding:
// 1. New Binding allow us to assign this to the object that we instantiate
function Person(name, age) {
  this.name = name;
  this.age = age;
  console.log(this); //refer to person1 information
}
const person1 = new Person("Xavier", 55);

// 2. Implicit Binding
const person = {
  name: "Karen",
  age: 40,
  hi() {
    console.log("hi " + this.name); //refer to person
  }
};
person.hi();

// 3. Explicit Binding - dictate where the this keyword should refer to
const person3 = {
  name: "Karen",
  age: 40,
  hi: function() {
    console.log("hi " + this.setTimeout);
  }.bind(window) //without bind, it will attach to person3 and get undefined
};
person3.hi();

// 4. Arrow functions - lexical scoping
const person4 = {
  name: "Karen",
  age: 40,
  hi: function() {
    var inner = () => {
      console.log("hi " + this.name);
    };
    return inner();
  }
};
person4.hi();
//without arrow, it will refer to window object and now it refers to person4
```

