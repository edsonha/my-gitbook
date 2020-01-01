# Functions

```javascript
FUNCTION ARGUMENTS
One or two arguments is the ideal case, and three should be avoided if possible. 
Anything more than that should be consolidated. 
Usually, if you have more than two arguments then 
your function is trying to do too much. In cases where it's not, 
most of the time a higher-level object will suffice as an argument.

Bad:
function createMenu(title, body, buttonText, cancellable) {
  // ...
}

Good:
function createMenu({ title, body, buttonText, cancellable }) {
  // ...
}

createMenu({
  title: "Foo",
  body: "Bar",
  buttonText: "Baz",
  cancellable: true
});
```

```javascript
FUNCTION SHOULD DO ONE THING
const clients = [
  { name: "B", isActive: false },
  { name: "A", isActive: true },
  { name: "C", isActive: true }
];

Bad:
function emailClients(clients) {
  clients.forEach(client => {
    if (client.isActive) {
      console.log(`emailing to ${client.name}`);
    }
  });
}

Good:
function emailActiveClients(clients) {
  clients.filter(isActiveClient).forEach(client => {
    console.log(`emailing to ${client.name}`);
  });
}

function isActiveClient(client) {
  return client.isActive === true;
}
```

```javascript
FUNCTIONS SHOULD ONLY BE ONE LEVEL OF ABSTRACTION
Bad:
const placeOrder = ({ order }) => {
  validateAvailability(order);
  
  const total = order.items.reduce(
    (item, totalAcc) =>
      totalAcc + item.unitPrice * item.units,
    0,
  );
  const invoiceInfo = getInvoiceInfo(order);
  const request = new PaymentService.Request({
    total,
    invoiceInfo,
  });
  const response = PaymentService.pay(request);
  
  sendInvoice(response.invoice);
  
  shipOrder(order);
};

Good:
const getTotal = order => {
  order.items.reduce(
    (item, totalAcc) =>
      totalAcc + item.unitPrice * item.units,
    0,
  );
};

const pay = (total, invoiceInfo) => {
  const request = new PaymentService.Request({
    total,
    invoiceInfo,
  });
  const response = PaymentService.pay(request);

  sendInvoice(response.invoice);
};

const payOrder = order => {
  const total = getTotal(order);
  const invoiceInfo = getInvoiceInfo(order);
  
  pay(total, invoiceInfo);
};

const placeOrder = ({ order }) => {
  validateAvailability(order);
  payOrder(order);
  shipOrder(order);
};
```

```javascript
REMOVE DUPLICATE CODE
Bad:
function showDeveloperList(developers) {
  developers.forEach(developer => {
    const expectedSalary = developer.calculateExpectedSalary();
    const experience = developer.getExperience();
    const githubLink = developer.getGithubLink();
    const data = {
      expectedSalary,
      experience,
      githubLink
    };

    render(data);
  });
}

function showManagerList(managers) {
  managers.forEach(manager => {
    const expectedSalary = manager.calculateExpectedSalary();
    const experience = manager.getExperience();
    const portfolio = manager.getMBAProjects();
    const data = {
      expectedSalary,
      experience,
      portfolio
    };

    render(data);
  });
}

Good:
function showEmployeeList(employees) {
  employees.forEach(employee => {
    const expectedSalary = employee.calculateExpectedSalary();
    const experience = employee.getExperience();

    const data = {
      expectedSalary,
      experience
    };

    switch (employee.type) {
      case "manager":
        data.portfolio = employee.getMBAProjects();
        break;
      case "developer":
        data.githubLink = employee.getGithubLink();
        break;
    }

    render(data);
  });
}
```

```javascript
SET DEFAULT OBJECTS WITH OBJECT.ASSIGN
Bad:
const menuConfig = {
  title: null,
  body: "Bar",
  buttonText: null,
  cancellable: true
};

function createMenu(config) {
  config.title = config.title || "Foo";
  config.body = config.body || "Bar";
  config.buttonText = config.buttonText || "Baz";
  config.cancellable =
    config.cancellable !== undefined ? config.cancellable : true;
}

createMenu(menuConfig);

Good:
const menuConfig = {
  title: "Order",
  // User did not include 'body' key
  buttonText: "Send",
  cancellable: true
};

function createMenu(config) {
  config = Object.assign(
    {
      title: "Foo",
      body: "Bar",
      buttonText: "Baz",
      cancellable: true
    },
    config
  );

  // config now equals: {title: "Order", body: "Bar", buttonText: "Send", cancellable: true}
  // ...
}

createMenu(menuConfig);
```

```javascript
DONT'T USE FLAGS AS FUNCTION PARAMETERS
Bad:
function createFile(name, temp) {
  if (temp) {
    fs.create(`./temp/${name}`);
  } else {
    fs.create(name);
  }
}

Good:
function createFile(name) {
  fs.create(name);
}

function createTempFile(name) {
  fs.create(`./temp/${name}`);
}
```

```javascript
AVOID SIDE EFFECTS (PART 1)
Bad:
// Global variable referenced by following function.
// If we had another function that used this name, now it'd be an array and 
// it could break it.
let name = "Ryan McDermott";

function splitIntoFirstAndLastName() {
  name = name.split(" ");
}

splitIntoFirstAndLastName();

console.log(name); // ['Ryan', 'McDermott'];

Good:
function splitIntoFirstAndLastName(name) {
  return name.split(" ");
}

const name = "Ryan McDermott";
const newName = splitIntoFirstAndLastName(name);

console.log(name); // 'Ryan McDermott';
console.log(newName); // ['Ryan', 'McDermott'];
```

```javascript
AVOID SIDE EFFECTS (PART 2)
Bad:
const addItemToCart = (cart, item) => {
  cart.push({ item, date: Date.now() });
};

Good:
const addItemToCart = (cart, item) => {
  return [...cart, { item, date: Date.now() }];
};
```

```javascript
DON'T WRITE TO GLOBAL FUNCTIONS
Bad:
Array.prototype.diff = function diff(comparisonArray) {
  const hash = new Set(comparisonArray);
  return this.filter(elem => !hash.has(elem));
};

Good:
class SuperArray extends Array {
  diff(comparisonArray) {
    const hash = new Set(comparisonArray);
    return this.filter(elem => !hash.has(elem));
  }
}
```

```javascript
FAVOR FUNCTIONAL PROGRAMMING OVER IMPERATIVE PROGRAMMING
Bad:
const programmerOutput = [
  {
    name: "Uncle Bobby",
    linesOfCode: 500
  },
  {
    name: "Suzie Q",
    linesOfCode: 1500
  },
  {
    name: "Jimmy Gosling",
    linesOfCode: 150
  },
  {
    name: "Gracie Hopper",
    linesOfCode: 1000
  }
];

let totalOutput = 0;

for (let i = 0; i < programmerOutput.length; i++) {
  totalOutput += programmerOutput[i].linesOfCode;
}

Good:
const totalOutput = programmerOutput.reduce(
  (totalLines, output) => totalLines + output.linesOfCode,
  0
);
```

```javascript
ENCAPSULTATE CONDITIONALS
Bad:
if (fsm.state === "fetching" && isEmpty(listNode)) {
  // ...
}

Good:
function shouldShowSpinner(fsm, listNode) {
  return fsm.state === "fetching" && isEmpty(listNode);
}

if (shouldShowSpinner(fsmInstance, listNodeInstance)) {
  // ...
}
```

```javascript
AVOID CONDITIONALS
Bad:
class Airplane {
  // ...
  getCruisingAltitude() {
    switch (this.type) {
      case "777":
        return this.getMaxAltitude() - this.getPassengerCount();
      case "Air Force One":
        return this.getMaxAltitude();
      case "Cessna":
        return this.getMaxAltitude() - this.getFuelExpenditure();
    }
  }
}

Good:
class Airplane {
  // ...
}

class Boeing777 extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude() - this.getPassengerCount();
  }
}

class AirForceOne extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude();
  }
}

class Cessna extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude() - this.getFuelExpenditure();
  }
}
```

```javascript
AVOID TYPE-CHECKING (PART 1)
Bad:
function travelToTexas(vehicle) {
  if (vehicle instanceof Bicycle) {
    vehicle.pedal(this.currentLocation, new Location("texas"));
  } else if (vehicle instanceof Car) {
    vehicle.drive(this.currentLocation, new Location("texas"));
  }
}

Good:
function travelToTexas(vehicle) {
  vehicle.move(this.currentLocation, new Location("texas"));
}
```

```javascript
AVOID TYPE-CHECKING (PART 2)
Bad:
function combine(val1, val2) {
  if (
    (typeof val1 === "number" && typeof val2 === "number") ||
    (typeof val1 === "string" && typeof val2 === "string")
  ) {
    return val1 + val2;
  }

  throw new Error("Must be of type String or Number");
}

Good:
function combine(val1, val2) {
  return val1 + val2;
}
```

