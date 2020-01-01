# Primitive Obsession

```javascript
//Problem:
class User {
  constructor(firstName, lastName, age, gender, block, streetName, unitNo, postalCode){
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.gender = gender
    this.block = block
    this.streetName = streetName
    this.unitNo = unitNo
    this.postalCode = postalCode
  }
}


//**Solution**:
class User {
  constructor(name, age, gender, address) {
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.address = address;
  }
}

class Name {
  constructor(first, last) {
    this.firstName = first;
    this.lastName = last;
  }
  
  getFormattedName() {
    return `${this.firstName} ${this.lastName}`;
  }
}

class Address {
  constructor(block, streetName, unitNo, postalCode) {
    this.block = block;
    this.streetName = streetName;
    this.unitNo = unitNo;
    this.postalCode = postalCode;
  }
}

const user1 = new User(
  new Name(first, last),
  age,
  gender,
  new Address("122", "Costa East Rd", "#19-02", "345643")
);
```

