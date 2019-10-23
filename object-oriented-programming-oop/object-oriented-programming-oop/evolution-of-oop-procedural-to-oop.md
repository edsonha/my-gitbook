# Evolution of OOP \(Procedural to OOP\)

Procedural - we have variable on one side and function on the other side. They are decoupled. One symptoms of procedural code is function that has many parameters.

```
let baseSalary = 1000
let overtime = 10
let rate = 20

function getWage(baseSalary, overtime, rate) {
    return baseSalary + (overtime * rate)
}
```

First step to OOP is to encapsulate, like below example. We group functionality together. We have state / data within the object and functions or methods acting on the state such as read or modify the state. "The best function are those with no parameter" - Uncle Bob as the fewer the parameter, the easier is to use and maintain the function. 

```
let employee = {
    baseSalary: 1000,
    overtime: 10,
    rate: 20,
    getWage: function() { //no parameter as they are properties of the object
        return this.baseSalary + (this.overtime * this.rate)
    }
};

employee.getWage();
```

The problem with above is that you repeat yourself to get 2nd, 3rd and so on employee wages. So, the next step is to create Factory Function or functions that act like factory and create objects for us.

```
function createElf(name, weapon) {
  return {
    name: name,
    weapon: weapon,
    attack: function() {
      return "atack with " + weapon;
    }
  }
}

const sam = createElf("Sam", "stone");
const peter = createElf("Peter", "bow");

console.log(sam.atack()); //We create Sam Elf that can attack stone
console.log(peter.atack()); //We create Peter Elf that can attack with bow
```

The problem with above is that if we have many elves, they will require space in our memory. In order to be efficient, we group the data separately. For example, name and weapon are unique so we can store each data in each memory space. But for method such as attach, they are pretty generic so they no need to be copied. The solution is prototypal inheritance.

```
//A. Manual Way
const elfFunctionsStore = {
  attack: function() {
    return "atack with " + this.weapon;
  }
};

function createElf(name, weapon) {
  return {
    name,
    weapon
  };
}

const sam = createElf("Sam", "fire");
sam.attack = elfFunctionsStore.attack;
sam.attack();

//B. Object.create()
const elfFunctionsStore = {
  attack: function() {
    return "atack with " + this.weapon;
  }
};

function createElf(name, weapon) {
  //Object.create creates __proto__ link
  let newElf = Object.create(elfFunctionsStore);
  console.log(newElf.__proto__); //without proto, it is just empty object
  newElf.name = name;
  newElf.weapon = weapon;
  return newElf;
}

const sam = createElf("Sam", "fire");
sam.attack();
```

Object.create creates a link between the elf-function-store and the new elf. So what we are essentially doing here is the true prototypal inheritance. However you won't see this out in most code bases. There was an old method that is even closer to the object oriented programming and that is using constructor function.

```
//A. Constructor Functions (Old)
function Elf(name, weapon) {
  this.name = name;
  this.weapon = weapon;
  var a = 5; //will not be attached to Elf because there is no "this"
  
  console.log("this", this);
  //this -> Elf {name: "Sam", weapon: "fire"}
  //this -> Elf {name: "Peter", weapon: "bow"}
}

Elf.prototype.attack = function() {
  return "atack with " + this.weapon;
};

const sam = new Elf("Sam", "fire");
console.log(sam.attack()); //attack with fire

const peter = new Elf("Peter", "bow");
console.log(peter.__proto__); //{attack: ƒ, constructor: ƒ}
```

In Elf.prototype.attack function, if we change it to arrow function, we will get undefined because arrow functions are lexical scoped. That is they defined "this" based on where they're read. And for above case, it is the global object who's calling attack right now. There's no object surrounding it other than the global object. But by using the regular function which is dynamically scoped that is it doesn't matter where it's written and it's about whoever calls it.

```
//A. Constructor Functions (New)
class Elf {
  constructor(name, weapon) {
    this.name = name;
    this.weapon = weapon;
  }
  
  attack() {
    return "atack with " + this.weapon;
  }
}

const fiona = new Elf("Fiona", "ninja stars");
console.log(fiona instanceof Elf); // true
const ben = new Elf("Ben", "bow");
fiona.attack();

```

