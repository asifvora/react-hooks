# An introduction to React Hooks
![image](https://github.com/asifvora/react-hooks/blob/master/react-hooks.png)

As the ReactJs library gets new updates, there are a lot of things being added and a few that are deprecated too. ReactJs is becoming more powerful day by day due to such updates. As a developer, you need to keep yourself up to date with new features coming out in every version.

# Have you heard about React Hooks?
Well, React Hooks, a feature which is available in React v16.7.0-alpha, is something awesome you should know about.

```
$ npm install react@16.7.0-alpha.0 --save
$ npm install react-dom@16.7.0-alpha.0 --save
```

## State Hook
This example renders a counter. When you click the button, it increments the value:

```js
import { useState } from 'react';

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

### Declaring multiple state variables
You can use the State Hook more than once in a single component:
```js
function ExampleWithManyStates() {
  // Declare multiple state variables!
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
  // ...
}
```

## Effect Hook
The Effect Hook, `useEffect`, adds the ability to perform side effects from a function component. It serves the same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in React classes, but unified into a single API.

For example, this component sets the document title after React updates the DOM:
```js
import { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
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


## Usage

To use hooks in a functional component!

```js
import React, { useState, useEffect, useReducer, memo } from 'react';
const style = {
  height: 60,
  width: 50,
  margin: 10,
}

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <>
      <p style={{ fontSize: 100 }}><b>{count}</b></p>
      <button style={style} onClick={() => setCount(count + 1)}>
        ➕
      </button>
      <button style={style} onClick={() => setCount(count - 1)}>
        ➖
      </button>
    </>
  );
}

function reducer(state, action) {
  switch (action.type) {
    case 'reset':
      return { count: action.payload };
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      // A reducer must always return a valid state.
      // Alternatively you can throw an error if an invalid action is dispatched.
      return state;
  }
}

function Counter({ initialCount }) {
  const [state, dispatch] = useReducer(reducer, initialState, { type: 'reset', payload: initialCount });

  return (
    <div>
      <p style={{ fontSize: 100 }}><b>{state.count}</b></p>
      <button style={style} onClick={() => dispatch({ type: 'reset', payload: initialCount })}>
        Reset
      </button>
      <button style={style} onClick={() => dispatch({ type: 'increment' })}>
        ➕
      </button>
      <button style={style} onClick={() => dispatch({ type: 'decrement' })}>
        ➖
      </button>
    </div>
  );
}

const MyComponentMemo = memo(function MyComponent(props) {
  return (
    <>
      <div style={{ fontSize: 50 }}>{props.name}</div>
    </>
  )
});

function MyComponent() {
  const [name, setName] = useState('😍');

  return (
    <div className="App">
      <header className="App-header">
        <div>
          <br />
          <input type="text" onChange={(e) => setName(e.target.value)} />
          <MyComponentMemo name={name} />
          {Counter({ initialCount: 0 })}
        </div>
      </header>
    </div >
  );
}

```

## Documentation

React Hooks API here: https://reactjs.org/docs/hooks-reference.html

- `useState`
- `useReducer`
- `useContext`
- `useMemo`
- `useCallback`
- `useEffect`
- `useRef`
- `useImperativeMethods`
- `useMutationEffect` _Note: currently identical to `useEffect`_
- `useLayoutEffect` _Note: currently identical to `useEffect`_

## Additional Hooks

The following hooks are also provided for convenience:

- `usePrevious` - Returns the previously rendered value you pass it

## ✌️ Rules of Hooks
Hooks are JavaScript functions, but they have two additional rules:

- _Note: Only call Hooks at the top level. Don’t try to call Hooks inside loops, conditions, or nested functions._
- _Note: Only call Hooks from React function components. Don’t try to call Hooks from regular JavaScript functions._


## Questions?🤔 
  
Hit me on [![Twitter URL](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/007_dark_shadow)
[![Medium](https://img.shields.io/badge/Medium-asifvora-brightgreen.svg)](https://medium.com/@asifvora)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-asifvora-blue.svg)](https://www.linkedin.com/in/asif-vora/) 
[![Instagram](https://img.shields.io/badge/Instagram-Asif%20Vora-green.svg)](https://www.instagram.com/007_dark_shadow/) 


## License

MIT License

Copyright (c) 2018 Asif Vora

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
