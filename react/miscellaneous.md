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

## 4. Selector and mapStateToProps

* Selector doesn't prevent re-render, selector prevent recalculation. 
* What prevent re-render is mapStateToProps. If the value is same, then mapStateToProps would not re-render your component. mapStatetoProps uses shouldComponentUpdate under the hood.
* If you try to memoize simple value\(non array and non object\), you probably don't need to because mapStateToProps can compare it easily for you.

Flow: action dispatch ---&gt; reducer update state ---&gt; if state change ---&gt; mapStateToProps run, receive latest state and compare current content with previous content ---&gt; if content is difference then re-render.

Reducer is not depending on mapStateToProps, it is the other way around, it is mapStateToProps depending on reducer. The value you saw in mapStateToProps is processing reducer state to produce new value, not mapStateToProps pass the value to reducer. 

Background:

1. If reducer return new value \(new object\), then this mean state change.
2. When state change, store will run every mounted component's mapStateToProps

It is crucial to explain why memoization is needed.

Imagine component A has some expensive calculation in its mapStateToProps:

```csharp
const mapState = (state) => { 
  return {
    profit: expensiveCalculation(state.num1,state.num2,state.num3)
  }; 
}
```

Now recall that any state change will run all mapStateToProps!

Imagine component B dispatch an action that return new state from reducer, even though this state change has nothing to do with component A, store will still use the same state to run component A's mapStateToProps, thus the expensiveCalculation run every single time for no obvious reason!

To prevent this, reselect library help us with memoization.

When mapStateToProps is called again due to any state update of any other components, Reselect will not run expensive calculation if the input values state.num1, state.num2, state.num3 remain the same with previous run.

## 4. Redux-Persist

Session storage persists throughout the session. So as long as our tab is open even if we refresh the page we'll still have access to what we've stored in session storage. Whereas if we close the page then we would lose whatever it is that we stored in session storage.

Local storage will persist until we clear it out. Meaning that if we close our window close our browser will always have access to it

