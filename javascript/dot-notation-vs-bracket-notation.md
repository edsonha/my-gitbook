# Dot Notation vs Bracket Notation

```
const newObject = {};

newObject.0 = "value 1" 
Result: Error as you cannot have number

newObject.key1 = "value 1" 
// newObject = {key1: "value 1"}

newObject["key1"] = "value 1" 
// newObject = {key1: "value 1"}

newObject["key2"] = "value 2"
// newObject = {key1: "value 1", key2: "value 2"}

newObject[0] = "value 0" 
//newObject = {0: "value 0", key1: "value 1", key2: "value 2"}

newObject["0"] = "value 00" 
//newObject = {0: "value 00", key1: "value 1", key2: "value 2"}

newObject["1"] = "value 01" 
//newObject = {0: "value 00", 1: "value 01", key1: "value 1", key2: "value 2"}
```

**Dot notation:**

* Property identifies can only be alphanumeric \(and `_` and `$`\)
* Property identifiers cannot start with a number.
* Property identifiers cannot contain variables.
* OK — `obj.prop_1`, `obj.prop$`
* Not OK — `obj.1prop`, `obj.prop name`

**Bracket notation:**

* Property identifiers have to be a String or a variable that references a String.
* It is okay to use variables, spaces, and Strings that start with numbers
* OK — `obj["1prop"]`, `obj["prop name"]`

