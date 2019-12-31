# Complex Condition

```text
//Problem:
if (!aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd)){
  charge = quantity * plan.summerRate;
}
else {
  charge = quantity * plan.regularRate + plan.regularServiceCharge;
}


//**Solution**:
if (isSummer()){
  charge = quantity * plan.summerRate;
} 
else {
  charge = quantity * plan.regularRate + plan.regularServiceCharge;
}

function isSummer() {
  return !aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd);
}
```

