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
function parseBetterJSAlternative(code) {
  const REGEXES = [
    // ...
  ];

  const statements = code.split(" ");
  const tokens = [];
  REGEXES.forEach(REGEX => {
    statements.forEach(statement => {
      // ...
    });
  });

  const ast = [];
  tokens.forEach(token => {
    // lex...
  });

  ast.forEach(node => {
    // parse...
  });
}

Good:
function parseBetterJSAlternative(code) {
  const tokens = tokenize(code);
  const syntaxTree = parse(tokens);
  syntaxTree.forEach(node => {
    // parse...
  });
}

function tokenize(code) {
  const REGEXES = [
    // ...
  ];

  const statements = code.split(" ");
  const tokens = [];
  REGEXES.forEach(REGEX => {
    statements.forEach(statement => {
      tokens.push(/* ... */);
    });
  });

  return tokens;
}

function parse(tokens) {
  const syntaxTree = [];
  tokens.forEach(token => {
    syntaxTree.push(/* ... */);
  });

  return syntaxTree;
}
```

