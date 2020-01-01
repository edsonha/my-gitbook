# Example of FP

```
const user = {
  name: 'Kim',
  active: true,
  cart: [{ name: 'orange', price: 20}],
  purchases: [{name: 'apple', price: 10}]
}

const item = {name: 'laptop', price: 200}

let amazonHistory = [];

const compose = (accumulatorFunction, currentFunction) => {
  return (...args) => accumulatorFunction(currentFunction(...args)); 
}

function purchaseItem(...fns) {
  return fns.reduce(compose)
}

function addItemToCart(user, item) {
  amazonHistory.push(user)
  const updatedCart = user.cart.concat([item]);
  return Object.assign({}, user, {cart: updatedCart})
}

function applyTaxToItems(user) {
  amazonHistory.push(user)
  const { cart } = user;
  const taxRate = 1.3;
  const updatedCart = cart.map(item => {
    return {
      name: item.name,
      price: item.price*taxRate
    }
  })
  return Object.assign({}, user, {cart: updatedCart})
}

function buyItem(user){
  amazonHistory.push(user)
  const updatedPurchases=user.purchases.concat(user.cart)
  return Object.assign({},user,{purchases:updatedPurchases})
}

function emptyCart(user) {
  amazonHistory.push(user)
  return Object.assign({}, user, {cart: []})
}

purchaseItem(emptyCart, buyItem, applyTaxToItems, addItemToCart)(user, item)
//amazonHistory
```

Why we're doing push to Amazon History? Isn't that state? Are we modifying state? Remember we can't just purely have pure functions in order for us to do anything with the program. We do have to mutate data and the idea of functional programming is to minimize those mutations.

Now the benefit of functional programming is it's really good at doing one to one data transformations. That is we have a piece of data and we have functions acting upon it.

