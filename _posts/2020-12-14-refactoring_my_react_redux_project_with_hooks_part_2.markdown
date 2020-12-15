---
layout: post
title:      "Refactoring my React/Redux Project with Hooks, Part 2"
date:       2020-12-14 02:21:57 -0500
permalink:  refactoring_my_react_redux_project_with_hooks_part_2
---


**Introduction:** In [my previous blog post](https://stevendcrouse.com/refactoring_my_react_redux_project_with_hooks_part_1), I introduced React hooks, explained how to use them and why, and showed how I refactored my Beach Journal project with them. I used React's `useState` and React Redux's `useDispatch` hooks to refactor a few of my components. If you haven't read that blog post yet, I would *highly* suggest doing so now, as it will get more complicated from here. In *this* blog post, Part 2, I will demonstrate how I used `useDispatch`, `useEffect`, and `useSelector` to refactor my App component.

## Recap: `useDispatch`
In my last blog post, I introduced the `useDispatch` hook and demonstrated how I used it to refactor a couple of components. Just to review, `useDispatch` essentially replaces React Redux's `connect` and `mapDispatchToProps` methods. Here's an example of how to use it, [based off of the official documentation](https://react-redux.js.org/api/hooks#usedispatch).

Without the `useDispatch` hook, your component might look like this:
```
import React, { Component } from 'react'
import { connect } from 'react-redux'

class CounterComponent extends Component {
  const { value, incrementCounter } = this.props
	
  render() {
    return (
      <div>
        <span>{value}</span>
        <button onClick={() => incrementCounter()}>
          Increment counter
        </button>
      </div>
    )
  }
}

const mapDispatchToProps = dispatch => {
  return {
    incrementCounter: () => dispatch({ type: 'increment-counter' })
  }
}

export default connect(null, mapDispatchToProps)(CounterComponent)
```

*With* the `useDispatch` hook, your component becomes much simpler:
```
import React from 'react'
import { useDispatch } from 'react-redux'

export const CounterComponent = ({ value }) => {
  const dispatch = useDispatch()

  return (
    <div>
      <span>{value}</span>
      <button onClick={() => dispatch({ type: 'increment-counter' })}>
        Increment counter
      </button>
    </div>
  )
}
```

## The `useEffect` hook
`useEffect` is a nifty little React hook that saves you a lot of hassle with component class lifecycle methods. The `useEffect` hook deals with any side effects in your components. According to the [React hooks documentation](https://reactjs.org/docs/hooks-effect.html), "you can think of [the] `useEffect` hook as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined". However, according to that documentation, [there is an important difference](https://reactjs.org/docs/hooks-effect.html#detailed-explanation):

> Unlike `componentDidMount` or `componentDidUpdate`, effects scheduled with `useEffect` don’t block the browser from updating the screen. This makes your app feel more responsive. The majority of effects don’t need to happen synchronously. In the uncommon cases where they do (such as measuring the layout), there is a separate [`useLayoutEffect`](https://reactjs.org/docs/hooks-reference.html#uselayouteffect) Hook with an API identical to `useEffect`.

I won't go into the `useLayoutEffect` hook here, as I did not use it to refactor my project. But feel free to check out that link if you're curious!

Conceptually, side effects can be separated into two categories: ones that don't require cleanup, and ones that do. Let's check out [this example of an effect that doesn't require cleanup](https://reactjs.org/docs/hooks-effect.html#example-using-classes). With class components, if you wanted to update your document's title every time you clicked a button, you might write something like this (again, all credit goes to the React developers for this example):

```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `You clicked ${this.state.count} times`;
  }
  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

When the document first loads, the title in your browser tab will say, "You clicked 0 times"; the same message will also be displayed in the document's body. When you click the button, the title and body will say, "You clicked 1 times", then "You clicked 2 times", etc.

Note that the code in the `componentDidMount` and `componentDidUpdate` lifecycle methods, is the same. Since we just want the same effect to happen after every render, ideally it should only be written in *one* method and called in *one* place. This is impossible with class components. However, it *is* possible with a functional component and the `useEffect` hook! Check this out (again, [from the React hooks documentation](https://reactjs.org/docs/hooks-effect.html#example-using-hooks)):

```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

Way simpler-looking, isn't it? What's happening here is that we're passing our intended effect (updating our document title to display a counter) as a function to `useEffect`. That effect is run after the component's initial render *and* after every update; this effectively combines `componentDidMount` and `componentDidUpdate` into one easy-to-use hook!

One major advantage here is that `useEffect` puts all of our code for an effect in one place, rather than splitting it up into different component lifecycle methods. Another advantage, [as shown by the React documentation](https://reactjs.org/docs/hooks-effect.html#tip-use-multiple-effects-to-separate-concerns), is that `useEffect` can be called multiple times, each time with a different effect. What this means is that you can now keep code related to one effect in one place *and* keep it separate from code related to other effects!

The React documentation also [explains how to use the `useEffect` hook on effects that require cleanup](https://reactjs.org/docs/hooks-effect.html#effects-with-cleanup) (i.e. effects that require `componentWillUnmount` in class components). For the sake of brevity - and because my project used an effect that did *not* require cleanup - I won't go into detail about it here. But to summarize it, you just have `useEffect` return an optional function that cleans up the effect.

### Refactoring the App component with `useEffect` and `useDispatch`

With all of that said, my App component needed to use `useEffect` in a more advanced way. When the component loaded, I wanted to execute the side effect of fetching all of the app's beach and journal entry data from the backend. However, I only wanted to do this *once*, after the initial render. So, how do you do that with `useEffect`?

It turns out that you can [specify an array of dependencies as a second, optional argument](https://reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects) to `useEffect`! The component will now only update when the value of at least one of those dependencies changes. In my case, the dependency was my `dispatch` variable.

With that in mind, my App component went (in part) from looking like this:
```
import React, { Component } from 'react';
import { connect } from 'react-redux';
import { fetchBeaches } from "./actions/beachActions";
// Other import statements

class App extends Component {
  componentDidMount() {
    this.props.fetchBeaches()
  }

  render() {
    // Other code
		
    return (
      {/* Page content */}
    );
  }
}

const mapDispatchToProps = dispatch => ({
  fetchBeaches: () => dispatch( fetchBeaches() )
});

export default connect(null, mapDispatchToProps)(App);
```

To looking like this:
```
import React, { useEffect } from 'react';
import { useDispatch } from 'react-redux';
import { fetchBeaches } from "./actions/beachActions";
// Other import statements

const App = () => {
  // Other code
	
  const dispatch = useDispatch();

  useEffect(
    () => dispatch(fetchBeaches()),
    [dispatch] 
  );
  
  return (
    {/* Page content */}
  );
}

export default App;
```

I could technically omit `dispatch` as a dependency, since it's *highly* unlikely to change. However, because I set `dispatch` to the return value of the `useDispatch` hook from React Redux - a separate library that React doesn't know about - I got this warning:

> React Hook useEffect has a missing dependency: 'dispatch'. Either include it or remove the dependency array  react-hooks/exhaustive-deps

There are also rare occasions where the value of `dispatch` could change, such as passing a new store to the `<Provider>` component. But more often than not, your code is fine without it. I'm of the opinion that it's better to include `dispatch` in the dependency array, just to be on the safe side and get rid of that warning. For more information, check out [this handy Stack Overflow article](https://stackoverflow.com/questions/56795607/what-are-the-cases-where-redux-dispatch-could-change).

## The `useSelector` hook
The `useSelector` hook is another handy feature provided by React Redux. Whereas `useDispatch` replaces `mapDispatchToProps`, `useSelector` virtually replaces `mapStateToProps`. I say "virtually" because although `useSelector` does a lot of the same things as `connect` and `mapStateToProps`, there are some important differences according to [the official documentation](https://react-redux.js.org/api/hooks). Perhaps most noticeably, `useSelector` can return *any* type of value, whereas `mapStateToProps` always returns a JavaScript object. In my next blog post, I will go into more detail about how `useSelector` differs from `connect` and `mapStateToProps`.

In my case, I wanted to display a loading message in my App component while the Beach Journal was retrieving its data from the backend.

This is how I implemented it with a class component:
```
import React, { Component } from 'react';
import './App.css';
import { connect } from 'react-redux';
import Navbar from "./components/Navbar";
// Other import statements

class App extends Component {
  // Other code
	
  render() {
    let pageContent;

    if (this.props.retrievingData) {
      pageContent = 
        <>
          <h1>Welcome to the Beach Journal!</h1>
          <p>Please wait while we load your saved beaches...</p>
        </>;
    } else {
      pageContent = 
        <>
          <Navbar />
          <section>
            {/* Other page content */}
          </section>
        </>
    }

    return (
      <div className="App">
        {/* Other JSX code */}
				
        {pageContent}
      </div>
    );
  }
}

const mapStateToProps = state => ({
  retrievingData: state.beachData.retrievingData
});

export default connect(mapStateToProps)(App);
```

This is how the App component looked after I refactored it with `useSelector`:
```
import React from 'react';
import './App.css';
import { useSelector } from 'react-redux';
import Navbar from "./components/Navbar";
// Other import statements

const App = () => {
  // Other code
	
  let pageContent;

  const retrievingData = useSelector( state => state.beachData.retrievingData );

  if (retrievingData) {
    pageContent = 
      <>
        <h1>Welcome to the Beach Journal!</h1>
        <p>Please wait while we load your saved beaches...</p>
      </>;
  } else {
    pageContent = 
      <>
        <Navbar />
        <section>
          {/* Other page content */}
        </section>
      </>
  }

  return (
    <div className="App">
      {/* Other JSX code */}
			
      {pageContent}
    </div>
  );
}

export default App;
```

Just like with `useEffect`, the `useSelector` hook accepts a selector function as an argument. According to [the React Redux documentation](https://react-redux.js.org/api/hooks#useselector), that function is "called with the entire Redux store state as its only argument" and returns the part of the state that you specify in the selector. As I mentioned earlier, that return value can be *anything*, whereas `mapStateToProps` *always* returns an object.

In my App component above, `mapStateToProps` would return something like:
```
{
  retrievingData: true // Or false
}
```

and (together with the `connect` method) pass that object as a prop to the App component.

But `useSelector` would just return `true` or `false`, which can then be saved to a variable within the App component itself. Way simpler - it uses less code and eliminates the need to pass in Redux state as props!

This is admittedly a very simple use case of `useSelector`. In the next blog post, I'll provide a more advanced example of how I used `useSelector` with the Reselect library and memoization in my BeachesContainer component.

## Putting it all together

When I put all of these hooks together, the App component went from looking like this:
```
import React, { Component } from 'react';
import './App.css';
import { connect } from 'react-redux';
import { fetchBeaches } from "./actions/beachActions";
import Navbar from "./components/Navbar";
// Other import statements

class App extends Component {
  componentDidMount() {
    this.props.fetchBeaches()
  }

  render() {
    let pageContent;

    if (this.props.retrievingData) {
      pageContent = 
        <>
          <h1>Welcome to the Beach Journal!</h1>
          <p>Please wait while we load your saved beaches...</p>
        </>;
    } else {
      pageContent = 
        <>
          <Navbar />
          {/* Other page content */}
        </>
    }

    return (
      <div className="App">
        {/* Other JSX */}
        {pageContent}
      </div>
    );
  }
}

const mapStateToProps = state => ({
  retrievingData: state.beachData.retrievingData
});

const mapDispatchToProps = dispatch => ({
  fetchBeaches: () => dispatch( fetchBeaches() )
});

export default connect(mapStateToProps, mapDispatchToProps)(App);
```

To looking like this:
```
import React, { useEffect } from 'react';
import './App.css';
import { useSelector, useDispatch } from 'react-redux';
import { fetchBeaches } from "./actions/beachActions";
import Navbar from "./components/Navbar";
// Other import statements

const App = () => {
  let pageContent;

  const dispatch = useDispatch();
  const retrievingData = useSelector( state => state.beachData.retrievingData );

  useEffect(
    () => dispatch(fetchBeaches()),
    [dispatch] 
  );
  
  if (retrievingData) {
    pageContent = 
      <>
        <h1>Welcome to the Beach Journal!</h1>
        <p>Please wait while we load your saved beaches...</p>
      </>;
  } else {
    pageContent = 
      <>
        <Navbar />
        <section>
          {/* Other page content */}
        </section>
      </>
  }

  return (
    <div className="App">
      {/* Other JSX */}
      {pageContent}
    </div>
  );
}

export default App;
```

> **Side note:** For the sake of brevity, I've only included the relevant parts of the App component. If you want to see the *entire* App component with its changes, [check out this Git commit](https://github.com/Sdcrouse/beach-journal-client/commit/9be5808dd32300c0534788112a86c39762cab331#diff-3d74dddefb6e35fbffe3c76ec0712d5c416352d9449e2fcc8210a9dee57dff67).

This is probably why the official documentation itself [recommends against refactoring existing, complicated components with hooks](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy). I made *all* of these changes in one commit because my code would have broken otherwise! In retrospect, it would have been better just to make a temporary file and use it to refactor my App component one step at a time.

## Conclusion
Congratulations, you've made it to the end of my long blog post! To summarize, I described how to use React's `useEffect` hook and React Redux's `useDispatch` and `useSelector` hooks. I then demonstrated how I used all three hooks to refactor my Beach Journal's App component.

`useEffect` greatly simplifies your React code by combining related code from separate side-effect-related lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`. It also lets you separate code for unrelated side effects. This makes your components much easier to understand and should therefore lead to fewer bugs.

`useDispatch` and `useSelector` virtually replace React Redux's `connect`, `mapDispatchToProps`, and `mapStateToProps` methods. (As I said, though, there are some important differences between how `useSelector` works, and how `connect` and `mapStateToProps` work; I will go into more detail in Part 3.) As with `useEffect` and other hooks, these greatly simplify your components, making them easier to read and less prone to bugs.

As I mentioned in the **Putting it all together** section above and in the previous blog post, I don't (in retrospect) recommend refactoring complicated components with hooks. If you still decide to do this, try to do it one step at a time with a temporary file. If you don't use a temporary file, you might realize that you'll have to make a *ton* of changes to your component(s) at once in order for your app not to break. And in so doing, you may accidentally introduce bugs.

In Part 3, the last blog post of the "Refactoring my React/Redux Project with Hooks" series, I will demonstrate how I used the `useSelector` and `useLocation` hooks, the Reselect library, and memoization to refactor my BeachesContainer component. Stay tuned, and thanks for reading!

## Resources
1. [Blog post: "Refactoring my React/Redux Project with Hooks, Part 1"](https://stevendcrouse.com/refactoring_my_react_redux_project_with_hooks_part_1)
2. [React Redux's `useDispatch` hook](https://react-redux.js.org/api/hooks#usedispatch)
3. [React's `useEffect` hook](https://reactjs.org/docs/hooks-effect.html)
4. [A detailed explanation of `useEffect` and how it differs from `componentDidMount` and `componentDidUpdate`](https://reactjs.org/docs/hooks-effect.html#detailed-explanation)
5. [React's `useLayoutEffect` hook](https://reactjs.org/docs/hooks-reference.html#uselayouteffect)
6. [Side effect example that doesn't require cleanup (class component)](https://reactjs.org/docs/hooks-effect.html#example-using-classes)
7. [Side effect example that doesn't require cleanup (hooks)](https://reactjs.org/docs/hooks-effect.html#example-using-hooks)
8. [Using multiple effects to separate concerns](https://reactjs.org/docs/hooks-effect.html#tip-use-multiple-effects-to-separate-concerns)
9. [Side effects that require cleanup](https://reactjs.org/docs/hooks-effect.html#effects-with-cleanup)
10. [How to optimize app performance by applying effects only when needed](https://reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects)
11. [Stack Overflow article explaining when React Redux's `dispatch` function could change](https://stackoverflow.com/questions/56795607/what-are-the-cases-where-redux-dispatch-could-change)
12. [Documentation for React Redux hooks](https://react-redux.js.org/api/hooks)
13. [React Redux's `useSelector` hook](https://react-redux.js.org/api/hooks#useselector)
14. [Git commit for refactoring the Beach Journal's App component with hooks](https://github.com/Sdcrouse/beach-journal-client/commit/9be5808dd32300c0534788112a86c39762cab331#diff-3d74dddefb6e35fbffe3c76ec0712d5c416352d9449e2fcc8210a9dee57dff67)
15. [Gradually adopting hooks vs. refactoring existing components with them](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy)
