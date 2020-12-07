---
layout: post
title:      "Refactoring my React/Redux Project with Hooks, Part 1"
date:       2020-12-07 01:14:26 -0500
permalink:  refactoring_my_react_redux_project_with_hooks_part_1
---


**Introduction:** When I created my React/Redux project, a Beach Journal app, I used class components to store state. In order to share state between components, I passed it as props to child components. If I wanted to use the same logic in multiple components, I wrapped them in a parent container. Stateful class components worked just fine for the project requirements, but [in 2018 Dan Abramov and the React team came up with a new and better feature](https://reactjs.org/docs/hooks-intro.html#video-introduction): React hooks! Shortly afterwards, [Redux and other libraries followed suit](https://react-redux.js.org/api/hooks). In these next couple of blog posts, I'll summarize what hooks are and demonstrate how I used them to refactor my Beach Journal app.

## What are hooks, and why would we use them?
Hooks solved three main problems that had been prevalent in React for years:

1. Many times, programmers would put a lot of stateful logic and side effects into one component, and usually all over the place because of React's component lifecycle methods. This made it difficult to test or break into smaller parts without using a separate library like Redux.
2. One way to solve the first problem was to create wrapper components (as I mentioned in the introduction) in order to share component logic and simplify the components. However, this inevitably led to "wrapper hell", i.e. components that were so deeply nested that the component structure was nearly impossible to understand!
3. Another problem was that class components themselves were difficult for programmers (and code compilers) to understand. For one thing, you need to understand JavaScript's `this` keyword in order to use them properly. Whereas functional components, while much simpler and easier to understand, were unable to store state.

All of these problems had one root cause: If you wanted to share stateful logic between components, you couldn't create anything simpler in React than a class component. Enter hooks. According to [the official documentation](https://reactjs.org/docs/hooks-intro.html#motivation), this is how hooks solve the above three problems:

1. "Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data), rather than forcing a split based on lifecycle methods."
    * Layman's terms: You can keep related code together without worrying about the React component lifecycle.
2. "Hooks allow you to reuse stateful logic without changing your component hierarchy."
    * Layman's terms: There's no longer any need to nest multiple components inside of wrapper components just to share logic, and thus no "wrapper hell".)
3. "Hooks let you use more of React’s features without classes."
    * Layman's terms: Pretty much self-explanatory. Instead of confusing class components, you can now use functional components with state!

Other benefits of using hooks include making your code easier to read and improving runtime performance.

I'll now delve into some of these hooks and show how I refactored my React components with them.

## The useState hook
The useState hook makes it much easier to use local state without a lot of the extra structure required by a class component.

To use [the example from the React resources](https://reactjs.org/docs/hooks-state.html), let's say you wanted to make a component that increases a counter by one every time you click a button. If you use a class component, you might do something like this:
```
import React from 'react';

class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
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

With the useState hook, however, you can change the component into a simpler functional component like this:
```
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

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

Now, instead of using a constructor to initialize local state, you can simply set a stateful `count` variable to `useCount(0)`. And instead of using a class component's `render` method and `setState`, you can update the value of `count` with `setCount`. The advantage here is that instead of updating your *entire state* just to change a piece of it, `useState` lets you "hook into" a *specific piece of your state* and update only that. It's much simpler and uses less code.

The new hook syntax will take a little getting used to, but it simplifies the structure of your components and makes them more readable!

## A note about using React hooks
Before we move on, there are a couple of "rules" of React hooks that you should be aware of. According to [the official documentation](https://reactjs.org/docs/hooks-rules.html), there are only two places where you can call hooks:

1. At the top level, i.e. not inside of loops, conditional statements, or nested functions. This allows React to correctly call your hooks "in the same order each time a component renders", as well as preserve state between multiple calls to `useState` and other hooks.
2. From inside of React functional components instead of regular JavaScript functions. (You can also call hooks from inside of custom hooks, but that's a topic for another time.) In addition to allowing React to work properly, this makes it much easier to find your component's stateful logic later.

I'll demonstrate how I refactored some of my components with `useState` shortly. But first, let's take a look at another hook, `useDispatch`. This one is provided by the React Redux library.

## The useDispatch hook
> **Note:** If you're unfamiliar with the React Redux library, you should [read over the basics of Redux here](https://redux.js.org/tutorials/essentials/part-1-overview-concepts#introduction) before moving on. You will also want to read up on [the React Redux library here](https://react-redux.js.org/introduction/quick-start), particularly the sections that focus on dispatching actions and using `mapDispatchToProps`.

...OK, now that you've read through all that, I'm glad you're back! So, let's look over the `useDispatch` hook. First of all, in order to update the state in your Redux store, you use React Redux to dispatch an action to a reducer. In order to get this to work, you have to write a `mapDispatchToProps` function with all of your dispatch actions, and you have to use React Redux's `connect` method to properly connect those dispatch actions to your component.

Thankfully, React Redux has a hook to simplify all that: `useDispatch`! Instead of doing all that setup that I mentioned above, all you need to do is use this one line of code within your functional component:
```
const dispatch = useDispatch()
```

That's literally it! You don't need `connect` or `mapDispatchToProps` at all. If you want to see an example of how this is used, [check out the official documentation](https://react-redux.js.org/api/hooks#usedispatch). However, I will also show how I applied `useDispatch` to my code.

### Refactoring JournalEntry.js with the useDispatch hook
Before I continue, I should note that it is now possible to initialize state in React class components just by using `state = {...}`. You don't need to use the class `constructor` method unless you want to initialize local state with props. This is how I structured all of my class components.

With that out of the way, I'll now demonstrate how I used `useDispatch` in my Beach Journal's JournalEntry component. Admittedly, I think I used `useDispatch` from the get go, since the JournalEntry component was always a functional component; I may not have realized at the time that it was a hook.

The JournalEntry component renders a journal entry's title, topics, date, and text. It also has a button for deleting that journal entry. Had I not used the `useDispatch` hook from the start, this is probably what the JournalEntry component would have looked like:
```
import React, { Component } from 'react';
import { connect } from 'react-redux';
import { deleteJournalEntry } from '../../actions/journalEntryActions';
import Button from 'react-bootstrap/Button';
import '../../App.css';

const JournalEntry extends Component {
  render() {
	
    const { id, beach_id, title, topics, date, entry_text, dispatch } = this.props;
	
    let topicsList;

    if(topics) {
      topicsList = <p>Topics: {topics}</p>;
    }

    const textParagraphs = entry_text.split("\n\n").map((paragraph, index) => <p key={index}>{paragraph}</p>);

    return (
      <>
        <br />
        <div className="journal-entry">
          <p><strong className="tertiary-labels">{title}</strong></p>
          {topicsList}
          <p>{date}</p>
          {textParagraphs}
          <Button variant="dark" onClick={() => deleteJournalEntry(id, beach_id)}>Delete this Journal Entry</Button>
        </div>
        <br />
      </>
    );
  }
};

const mapDispatchToProps = dispatch => {
  deleteJournalEntry: (id, beach_id) => dispatch( deleteJournalEntry(id, beach_id) )
}

export default connect(null, mapDispatchToProps)(JournalEntry);
```

Whereas this is how it looks with `useDispatch`:
```
import React from 'react';
import { useDispatch } from 'react-redux';
import { deleteJournalEntry } from '../../actions/journalEntryActions';
import Button from 'react-bootstrap/Button';
import '../../App.css';

const JournalEntry = ({ id, beach_id, title, topics, date, entry_text }) => {
  const dispatch = useDispatch();
  let topicsList;

  if(topics) {
    topicsList = <p>Topics: {topics}</p>;
  }

  const textParagraphs = entry_text.split("\n\n").map((paragraph, index) => <p key={index}>{paragraph}</p>);

  return (
    <>
      <br />
      <div className="journal-entry">
        <p><strong className="tertiary-labels">{title}</strong></p>
        {topicsList}
        <p>{date}</p>
        {textParagraphs}
        <Button variant="dark" onClick={() => dispatch( deleteJournalEntry(id, beach_id) )}>Delete this Journal Entry</Button>
      </div>
      <br />
    </>
  );
};

export default JournalEntry;
```

Way simpler, don't you think? But now things are about to get REALLY fun. Let's see what happens when we use `useState` and `useDispatch` together in the same component!

## Using the `useState` and `useDispatch` hooks together
As I mentioned in [a previous blog post](https://stevendcrouse.com/beach_journal_my_final_and_most_complicated_project), when you use the Beach Journal app, you can navigate to a beach's page and create journal entries for it. In order for this to work, I made a JournalEntryForm component. When the journal entry was successfully created, the Beach Journal app would redirect to that same beach's page.

Here is what the JournalEntryForm component looked like when it was a stateful class component:
```
import React, { Component } from 'react';
import { connect } from 'react-redux';
import { createJournalEntry } from '../../actions/journalEntryActions';
import { Redirect } from 'react-router-dom';
import Form from 'react-bootstrap/Form';
import { LabeledInput, LabeledTextarea } from '../LabelsAndInputs';
import '../../App.css';
import Container from 'react-bootstrap/Container';
import Button from 'react-bootstrap/Button';

class JournalEntryForm extends Component {
  state = {
    journalEntry: {
      beach_id: this.props.beachId,
      date: '',
      title: '',
      topics: '',
      entry_text: ''
    },
    errorMessage: '',
    redirect: false
  };

  handleChange = event => {
    this.setState({
      journalEntry: {
        ...this.state.journalEntry,
        [event.target.name]: event.target.value
      }
    })
  }

  handleSubmit = event => {
    const { date, entry_text } = this.state.journalEntry;
    
    event.preventDefault();

    if (date === '' || entry_text === '') {
      this.setState({
        errorMessage: "One or more required fields have not been filled out."
      });
    } else {
      this.props.createJournalEntry(this.state);
      this.setState({
        redirect: true
      })
    }
  }

  redirectToBeach = beach_id => {
    // Stretch goal: See if I can just replace the form with all of the journal entries, instead of redirecting.

    if (this.state.redirect) {
      return (
        <Redirect 
          to={{
            pathname: `/beaches/${beach_id}`,
            state: {successMessage: "Journal entry successfully created!"}
          }}
        />
      )
    }
  }
  
  render() {
    const { date, title, topics, entry_text, beach_id } = this.state.journalEntry;

    return (
      <Container className="journal-entry-form">
        {this.redirectToBeach(beach_id)}

        <h3>New Journal Entry</h3>
        <p><strong>* </strong><span className="required-field">Required field</span></p>

        {this.state.errorMessage &&
          <h4>{this.state.errorMessage}</h4>
        }

        <Form onSubmit={this.handleSubmit}>
          <LabeledInput
            inputName="date"
            inputValue={date}
            labelClass="required-field"
            labelText="Date:"
            onChange={this.handleChange}
            required={true}
          />
          <LabeledInput
            inputName="title"
            inputValue={title}
            labelText="Title:"
            onChange={this.handleChange}
          />
          <LabeledInput
            inputName="topics"
            inputValue={topics}
            labelText="Topics:"
            onChange={this.handleChange}
          />
          <LabeledTextarea
            inputName="entry_text"
            inputValue={entry_text}
            labelClass="required-field"
            labelText="Entry Text:"
            onChange={this.handleChange}
            required={true}
            colSize={10}
            rows="15"
          />
          <Button type="submit">Write this Journal Entry!</Button>
        </Form>
      </Container>
    )
  }
}

const mapDispatchToProps = dispatch => ({
  createJournalEntry: entryData => dispatch(createJournalEntry(entryData))
});

export default connect(null, mapDispatchToProps)(JournalEntryForm);
```

And here is what the JournalEntry form component looked like after I refactored it with `useState` and `useDispatch`:
```
import React, { useState } from 'react';
import { useDispatch } from 'react-redux';
import { createJournalEntry } from '../../actions/journalEntryActions';
import { Redirect } from 'react-router-dom';
import Form from 'react-bootstrap/Form';
import { LabeledInput, LabeledTextarea } from '../LabelsAndInputs';
import '../../App.css';
import Container from 'react-bootstrap/Container';
import Button from 'react-bootstrap/Button';

const JournalEntryForm = props => {
  const dispatch = useDispatch();
  
  const [journalEntry, setJournalEntry] = useState({
    beach_id: props.beachId,
    date: '',
    title: '',
    topics: '',
    entry_text: ''
  });

  const { date, title, topics, entry_text, beach_id } = journalEntry;
  
  const [errorMessage, setErrorMessage] = useState('');
  const [redirect, setRedirect] = useState(false);
  
  const handleChange = event => {
    setJournalEntry({
      ...journalEntry,
      [event.target.name]: event.target.value
    })
  }

  const handleSubmit = event => {
    event.preventDefault();

    if (date === '' || entry_text === '') {
      setErrorMessage("One or more required fields have not been filled out.");
    } else {
      dispatch(createJournalEntry({ journalEntry }));
      setRedirect(true);
    }
  }

  const redirectToBeach = beach_id => {
	  // Stretch goal: See if I can just replace the form with all of the journal entries, instead of redirecting.

    if (redirect) {
      return (
        <Redirect 
          to={{
            pathname: `/beaches/${beach_id}`,
            state: {successMessage: "Journal entry successfully created!"}
          }}
        />
      )
    }
  }

  return (
    <Container className="journal-entry-form">
      {redirectToBeach(beach_id)}

      <h3>New Journal Entry</h3>
      <p><strong>* </strong><span className="required-field">Required field</span></p>

      {errorMessage && <h4>{errorMessage}</h4>}

      <Form onSubmit={handleSubmit}>
        <LabeledInput
          inputName="date"
          inputValue={date}
          labelClass="required-field"
          labelText="Date:"
          onChange={handleChange}
          required={true}
        />
        <LabeledInput
          inputName="title"
          inputValue={title}
          labelText="Title:"
          onChange={handleChange}
        />
        <LabeledInput
          inputName="topics"
          inputValue={topics}
          labelText="Topics:"
          onChange={handleChange}
        />
        <LabeledTextarea
          inputName="entry_text"
          inputValue={entry_text}
          labelClass="required-field"
          labelText="Entry Text:"
          onChange={handleChange}
          required={true}
          colSize={10}
          rows="15"
        />
        <Button type="submit">Write this Journal Entry!</Button>
      </Form>
    </Container>
  )
}

export default JournalEntryForm;
```

Admittedly, it's hard to see the benefit here, since both versions have over 100 lines of code. However, this refactoring shortened my code by 15 lines, a 12.4% decrease!

Similarly, I also refactored my NewBeachPage component with `useDispatch` and `useState`. For the sake of brevity, I won't show those changes here.

## A word of caution
In retrospect, I would actually advise *against* refactoring your existing class components with hooks, unless:

1. You only need to refactor with *one* hook,
2. You *really* need to optimize your app for speed and performance, or
3. Your component is small enough that it can be refactored easily.

The reason I'm saying this is because quite a few of my components (including the JournalEntryForm) needed to be refactored with two or three hooks. However, I often couldn't refactor with one hook at a time without breaking my app. As a result, I made a lot of changes in a few commits, which can easily create bugs unless you're *super* careful. This will be especially evident in Part 2, when I discuss how I refactored my App and BeachesContainer components. In fact, [the React documenation *itself* advises against doing this](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy)! 

In the future, I'll create new components with hooks from the get go, rather than try to convert class components into functional components with hooks. "If it ain't broke, don't fix it", as they say.

## Conclusion
Despite the fact that it isn't recommended, I refactored my Beach Journal's class components into functional components with hooks. In the process, I learned a lot about how hooks work (and *don't* work). While I wouldn't suggest doing this with super-complicated components, it can be a good exercise to refactor a small component with hooks to get a feel for them.

The `useState` hook made it much easier to work with local state in a component, and `useDispatch` prevented the need to use `connect` and `mapDispatchToProps`. In both cases, I was able to shrink my components and make them easier to read. And if I'm not mistaken, all of these changes together made the Beach Journal run a little bit faster.

In Part 2, I will go over how I refactored a few of my other components with React's `useEffect` hook, React Router DOM's `useLocation` hook, React Redux's `useSelector` hook, the Reselect library, and memoization. Stay tuned, readers!

## Resources
1. [GitHub repository for the Beach Journal app](https://github.com/Sdcrouse/beach-journal-client)
2. [Video introduction to React hooks](https://reactjs.org/docs/hooks-intro.html#video-introduction)
3. [React Redux hooks](https://react-redux.js.org/api/hooks)
4. [Why React hooks were invented](https://reactjs.org/docs/hooks-intro.html#motivation)
5. [Using the `useState` hook](https://reactjs.org/docs/hooks-state.html)
6. [Rules of Hooks](https://reactjs.org/docs/hooks-rules.html)
7. [Introduction to Redux](https://redux.js.org/tutorials/essentials/part-1-overview-concepts#introduction)
8. [Introduction to React Redux](https://react-redux.js.org/introduction/quick-start)
9. [Using the `useDispatch` hook](https://react-redux.js.org/api/hooks#usedispatch)
10. [Beach Journal blog post](https://stevendcrouse.com/beach_journal_my_final_and_most_complicated_project)
11. [Why it's better to adopt hooks gradually instead of refactoring with them](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy)
