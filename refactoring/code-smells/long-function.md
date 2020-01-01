# Long Function

```text
//Problem:
function printOwing(invoice) {
  printBanner();
  let outstanding = calculateOutstanding();

  //print details
  console.log(`name : ${invoice.customer}`);
  console.log(`amount : ${outstanding}`);
}


//**Solution**:
function printOwing(invoice) {
  printBanner();
  let outstanding = calculateOutstanding();
  printDetails(customer, outstanding)
}

function printDetails(customer, outstanding){
  console.log(`name : ${customer}`);
  console.log(`amount : ${outstanding}`);
}
```

