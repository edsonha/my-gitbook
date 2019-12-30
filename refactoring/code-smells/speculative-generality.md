# Speculative Generality

```text
//Problem:
class Delivery {
  rating(aDriver) {
    return moreThanFiveLateDeliveries(aDriver) ? 1 : 5;
  }
  moreThanFiveLateDeliveries(aDriver) {
    return aDriver.numberOfLateDeliveries > 5;
  }
}


//**Solution**:
class Delivery {
  rating(aDriver) {
    return aDriver.numberOfLateDeliveries > 5 ? 1 : 5;
  }
}
```

