# Extra

```javascript
class Animal {
  talk() {
    console.log("?");
  }
}

class Bird extends Animal {
  talk() {
    return `tweet tweet`;
  }
  fly() {
    console.log("flap flap");
  }
}

class Parrot extends Bird {
  state = {
    happinness: 0
  };
  talk(item) {
    console.log(`${super.talk()} with a ${item}`);
  }
  sing(loud) {
    return (this.state.happinness += loud);
  }
}

var a = new Animal();
var b = new Bird();
var p = new Parrot();

a.talk(); //?
b.talk(); //tweet tweet
b.fly(); //flap flap
p.talk("cracker"); //tweet tweet with a cracker
p.fly(); //flap flap
p.sing(50); //50
```

```javascript
function createElf(name, weapon) {
  return {
    name: name,
    weapon: weapon,
    position: 100,
    run: function(speed) {
      return (this.position += speed);
    }
  };
}

const sam = createElf("Sam", "stone");
sam; //{name: "Sam", weapon: "stone", position: 100, run: ƒ}
sam.run(10); //110
```

