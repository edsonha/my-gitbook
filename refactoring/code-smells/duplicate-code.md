# Duplicate Code

```text
//Problem:
class MedicalRecord {
  constructor() {
    this.dDateArchived = null;
    this.bArchived = false;
  }

  archiveRecord() {
    this.bArchived = true;
    this.dDateArchived = Date.now();
  }

  closeRecord() {
    this.bArchived = true;
    this.dDateArchived = Date.now();
  }
}


//**Solution**:
class MedicalRecord {
  constructor() {
    this.dDateArchived = null;
    this.bArchived = false;
  }

  archiveRecord() {
    this._switchToArchived();
  }

  closeRecord() {
    this._switchToArchived();
  }

  _switchToArchived() {
    this.bArchived = true;
    this.dDateArchived = Date.now();
  }
}
```

