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

