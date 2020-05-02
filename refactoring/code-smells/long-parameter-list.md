# Long Parameter List

```javascript
//Problem:
function getInvoices(startDate, endDate) {
  //to pull invoices for that duration
}


//**Solution**:
function getInvoices(DateRange) {
  //to pull invoices for that duration
}

class DateRange {
  constructor(start, end) {
    this.startDate = start;
    this.endDate = end;
  }
}
```

```javascript
//Problem:
function availableVacation(anEmployee, grade) {
  // calculate vacation...
}

availableVacation(anEmployee, anEmployee.grade);


//**Solution**:
function availableVacation(anEmployee) {
  const grade = anEmployee.grade;
  // calculate vacation...
}

availableVacation(anEmployee);
```

