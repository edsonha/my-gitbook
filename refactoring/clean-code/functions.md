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

