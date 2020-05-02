# Double Negative

```javascript
//Problem:
class Customer {
  constructor() {
    this.nBalance = 0;
  }

  isNotFlagged() {
    return this.nBalance < 30;
  }
}

class Order {
  checkout(aProducts, oCustomer) {
    if (!oCustomer.isNotFlagged()) {
      // the customer account is flagged
      // log some errors and return
      return;
    }
    // normal order processing
  }
}


//**Solution**:
class Customer {
  constructor() {
    this.nBalance = 0;
  }

  isFlagged() {
    return this.nBalance >= 30;
  }
}

class Order {
  checkout(aProducts, oCustomer) {
    if (oCustomer.isFlagged()) {
      // the customer account is flagged
      // log some errors and return
      return;
    }
    // normal order processing
  }
}
```

