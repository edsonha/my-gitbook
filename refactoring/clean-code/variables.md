# Variables

```javascript
NO MAGIC NUMBER
Bad:
// What the heck is 86400000 for?
setTimeout(blastOff, 86400000);

Good:
// Declare them as capitalized named constants.
const MILLISECONDS_IN_A_DAY = 86400000;

setTimeout(blastOff, MILLISECONDS_IN_A_DAY);
```

```javascript
USE EXPLANATORY VARIABLE
Bad:
const address = "One Infinite Loop, Cupertino 95014";
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
saveCityZipCode(
  address.match(cityZipCodeRegex)[1],
  address.match(cityZipCodeRegex)[2]
);

Good:
const address = "One Infinite Loop, Cupertino 95014";
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
const [, city, zipCode] = address.match(cityZipCodeRegex) || []; 
//always make sure you have array even if the address is ""
saveCityZipCode(city, zipCode);
```

```javascript
USE DEFAULT ARGUMENTS INSTEAD OF SHORT CIRCUITING OR CONDITIONALS
Bad:
function createMicrobrewery(name) {
  const breweryName = name || "Hipster Brew Co.";
  // ...
}

Good:
function createMicrobrewery(name = "Hipster Brew Co.") {
  // ...
}
```

