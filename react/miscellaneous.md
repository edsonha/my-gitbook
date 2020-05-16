# Best Practices

## 1. setState is Async function

That is why setState is always one step behind console.log. The solution is to have callback inside the setState function like this:

```csharp
this.setState({ searchField: event.target.value }, () =>
    console.log(this.state)
);
```

## 2. Batch multiple set state calls

React, instead of calling setState one by one, will batch the setState call together and update them all into one single update for performance. Because of this, React does not guarantee that we update the state that this going to work or have the latest version of the state because setState is asynchronous \(we let the React decide when to update the state\). So there is a rule that if you are using modifying the this.state directly, it is better to use \(prevState, prevProps\).

```csharp
this.setState((prevState, prevProps) => ({ numbers: prevState.counter + 1}));
```

## 3. Constructor or not

If you are using this.props inside the constructor, the best practice is to call the constructor and super by passing props inside the parameter. 

If you are not using this.props, we can use alternate class syntax. No constructor, just state.

```csharp
state = {
    title: "Meaning of Life" 
}
```

## 3. ShouldComponentUpdate

ShouldComponentUpdate can improve improvement by selecting if the component should update or not. Return false \(No changes to state or props\) will not cause the component to move to the next phase of render and componentDidUpdate. Return true \(Changes to state or props\) will cause the component to render and componentDidUpdate. Because the idea is when the parent component \(App\) is re-render, it will trigger a chain reaction that also re-render children component.

```csharp
shouldComponentUpdate(nextProps, nextState) {
    console.log("shouldComponentUpdate!", nextProps);
    return nextProps.text !== this.props.text;
}
```

