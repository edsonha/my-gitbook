# Christmas Tree Code

```text
//Problem:
class Security {
  constructor(securityChecker) {
    this.securityChecker = securityChecker;
  }

  hasAccess(user, permission, exemptions) {
    let permission = false;
    if (user !== null) {
      if (permission !== null) {
        if (exemptions.length === 0) {
          if (
            this.securityChecker.checkPermission(
              user,
              permission,
              exemptions
            )
          ) {
            permission = true;
          }
        }
      }
    }
    return permission;
  }
}


//**Solution**:
class Security {
  constructor(securityChecker) {
    this.securityChecker = securityChecker;
  }

  hasAccess(user, permission, exemptions) {
    if (user === null || permission === null) {
      return false;
    }
    if (exemptions.contains(permission)) {
      return true;
    }
    return this.securityChecker.checkHasPermission(user, permission);
  }
}
```

