# Instantiation

    class Player {
      constructor(name, type) {
        // console.log("player", this);
        this.name = name;
        this.type = type;
      }

      introduce() {
        console.log(`Hello my name is ${this.name}. I am a ${this.type}`);
      }
    }

    class Wizard extends Player {
      constructor(name, type) {
        super(name, type); // to get access to the Player class
        // console.log("wizard", this);
      }

      play() {
        console.log(`Weee I am ${this.type}`);
      }
    }

    const player1 = new Player("Sally", "Female"); //'this' refer to the Player class
    const wizard1 = new Wizard("Sally2", "Healer"); //'this' refer to the Wizard class

    console.log(player1 instanceof Wizard) //false
    console.log(player1 instanceof Player) //true
    console.log(wizard1 instanceof Player) //true
    console.log(wizard1 instanceof Wizard) //true

An instance happens when we call the class and we create an object out of this class with the "new" keyword. This process is called instantiation where we are instantiating from a class.

When we "extends" \(inheritance\), in JS, we don't actually copy the functionality from super-class to subclass. Instead, it simply links up the prototype chain. So whenever it doesn't find something, lets say of the Wizard class, it is going to look up to the Player super-class. So it is creating this efficient linking or reference in JS using prototypal inheritance. In other language like Java and C++, it actually copy objects, so it is less in term of memory efficiency.

