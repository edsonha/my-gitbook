# Miscellaneous

## 1. setState is Async function

That is why setState is always one step behind console.log. The solution is to have callback inside the setState function like this:

```csharp
this.setState({ searchField: event.target.value }, () =>
    console.log(this.state)
);
```

