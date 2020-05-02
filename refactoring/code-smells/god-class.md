# God Class

```javascript
//Problem:
class CustomerService {
  calculateOrderDiscount(aProducts, oCustomer) {
    // do work
  }
  isValidCustomer(oCustomer, oOrder) {
    // do work
  }
  gatherOrderErrors(aProducts, oCustomer) {
    // do work
  }
  register(oCustomer) {
    // do work
  }
  forgotPassword(oCustomer) {
    // do work
  }
}


//**Solution**:
class CustomerOrderService {
  calculateOrderDiscount(aProducts, oCustomer) {
    // do work
  }
  isValidCustomer(oCustomer, oOrder) {
    // do work
  }
  gatherOrderErrors(aProducts, oCustomer) {
    // do work
  }
}

class CustomerRegistrationService {
register(oCustomer) {
    // do work
  }
  forgotPassword(oCustomer) {
    // do work
  }
}
```

