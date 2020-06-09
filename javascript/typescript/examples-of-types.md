# Examples of Types

```javascript
//1. boolean
let isCool: boolean = false;

//2. number
let age: number = 56;

//3. string
let eyeColor: string = "brown";
let favoriteQuote: string = `I'm not old, I'm only ${age}`;

//4. Array
let pets: string[] = ["cat", "mouse", "dragon"];
let pets2: Array<string> = ["pig", "lion", "dragon"];

//Object
let wizard: object = { name: "john" }

//5. Tuple - a syntax that has different types inside it
let basket: [string, number, boolean];
basket = ["basketball", 10, true];
basket = ["basketball", 10]; // will error because it expect boolean as the 3rd item

//6. Enum - allows us to define a set of named constant 
//(a way of giving more friendly names to sets of numeric values). 
//Example define direction like up, down, right and left and have each direction 
//has a value associated with it
enum Size {
  Small = 1,
  Medium, // infer as 2 even though no value is given
  Large
}
let sizeName: string = Size[2];
let sizeName2: string = Size[1];
let sizeName3: string = Size[4];
let sizeName4: number = Size.Large;
let sizeName5: number = Size.Regular; // cannot complile as Regular is not defined
console.log(sizeName); // Displays 'Medium' as its value is 2
console.log(sizeName2); // Displays 'Small' as its value is 1
console.log(sizeName3); // Display 'undefined' as there is no value 4
console.log(sizeName4); // Display 3 as the value of Large

//7. Any - be careful of using as it eliminates the benefit of using TS
let whatever: any = "aaaaghhhhhh noooooo!";

//8. void - function that does not return anything
let sing = (): void => {
  console.log("Lalalala");
  // return "Lala"; //give error because it is returning
};

//9. null and undefined
let meh: undefined = undefined;
let noo: null = null;

//10. never - a function that never return and doesn't have 
//reachable endpoint, usually throws error
let error = (): never => {
  throw Error("blah!");
};

//11. Type Assertions:
let x = 3;
x = "hello"; //give error because automatimally detects x is a number.

let ohhithere: any = "OH HI THERE";
let strLength: number = (ohhithere as string).length;

interface CatArmy {
  count: number;
  type: string;
  magic?: string;
}
let dog = {} as CatArmy; 
//without "as CatArmy", you will not be able to access dog.count
dog.count;

//12. Interface - create your own new type for an object. In the example below, 
//you are telling that the "robots" parameter to have all the properties and types 
//indicated in RobotArmy
interface RobotArmy {
  count: number;
  type: string;
  magic?: string; //with ?: it indicates that it may or may not get the property
}
//interface is similar to type with main difference: interface creates a new name 
//that we can use everywhere whereare type does not create a new name
type RobotArmy2 = {
  count: number;
  type: string;
  magic?: string;
};

let fightRobotArmy = (robots: RobotArmy) => {
  console.log("FIGHT!");
};
fightRobotArmy({ count: 1, type: "dragon" }); //can still pass without magic 

//function above is same as saying below
let fightRobotArmy2 = (robots: {
  count: number;
  type: string;
  magic: string;
}) => {
  console.log("FIGHT!");
};

//13. Function
let fightRobotArmyF = (robots: RobotArmy): void => {
  console.log("FIGHT!");
};
let fightRobotArmy2F = (robots: {
  count: number;
  type: string;
  magic?: string;
}): void => {
  console.log("FIGHT!");
};

//14. Classes
class Animal {
  private sing: string;
  public sang: string = "lalala";
  constructor(sound: string) {
    this.sing = sound;
  }
  greet(): string {
    return "Hello, " + this.sing;
  }
}
let lion = new Animal("Lion");
console.log(lion.sing); //give error as it is private class
console.log(lion.sang); //return "lalala"
console.log(lion.greet()); //return "Hello, Lion"

//15. Union Type - can be string or number or boolean
let confused: string | number = "hello";
```

