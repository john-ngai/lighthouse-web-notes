# Lighthouse Labs - Web Development Bootcamp - Jan 2022 - W06D5

## Installing Node

### NVM Cheatsheet

* List the local versions of Node.js using `nvm ls`.
* List the versions of Node.js that are available to install using `nvm ls-remote`.
* Install an available version of Node.js using `nvm install <version>`.
* Switch between Node.js versions using `nvm use <version>`.

<br><br>

## JSX in React

### React: Behind the Scenes

#### React.creatElement

Creating a React element with JSX means defining the type of element and any properties that we want to pass to it.

**JSX:**

```javascript
const element = <h2 className="name">Name</h2>
```

The code above is run through a tool that knows how to turn JSX into JavaScript. The tool produces a JavaScript expression that creates a React element using `React.createElement`.

**JavaScript:**

```javascript
const element = React.createElement("h2", {
  className: "name"
}, "Name")
```

<br><br>

## JSX Rules

### Rule #1

All tags must be closed. There are two ways to close a tag.

* Use two tags (an open tag and a close tag - e.g. `<div>...</div>`).
* Use one self-closing tag (e.g. `<img />` ).

### Rule #2

A child tag must close before its parent.

```javascript
<div>
  <li>
    <ul>
    </ul>
  </li>
</div>
```

### Rule #3

All JSX expressions must result in one root level element. A function can only return one value.

```javascript
return (
  <div>
    <input />
  </div>
);

/* becomes */

return React.createElement("div", null, React.createElement("input", null));
```

### Rule #4

No HTML comments.

```javascript
return (
  <div>
    <!--- Not allowed --->
    {/* Allowed */}
  </div>
);
```

<br><br>

## Navigating React App Files

### public Folder

```
./public/
  favicon.ico
  index.html  
  logo192.png  
  logo512.png  
  manifest.json  
  robots.txt
```

The public/ folder contains elements that will be accessible to the browser. The most important file in this folder is the index.html file since it is where the React app will attach itself.

### src Folder

```
./src/
  App.css  
  App.js  
  App.test.js  
  index.css  
  index.js  
  logo.svg  
  reportWebVitals.js  
  setupTests.js
```

The src/ folder contains all of the code for our app.

<br><br>

## Creating React Components

* Type `import React from 'react';` when using an older version of React (before v17).
* Functional components are declared using a capital letter instead lowercase (e.g. `function Navigation() {}`).
* Components can be exported using `export default Navigation;`.
* Component files should be organized inside a `components/` folder inside `src/`.

<br><br>

## Connecting Our Components

### Importing Our Components

We use the `import .. from ..` syntax, which is from `ES6` standard.

```javascript
// Example

import React from 'react';
import Navigation from './components/Navigation'
import Profile from './components/Profile'
```

### Showing Our Components

* The way to show components in JSX is to wrap the name of what we imported between <>.
* For example, a Navigation component could be called using the `<Navigation />` or `<Navigation></Navigation>` syntax.

<br><br>

## Event Handling in React

We can attach event handlers to React elements and pass a reference to a function directly or indirectly.

```javascript
// Example 1

function Button() {
  return (
     <button onClick={() => console.log("Button Clicked")}>
      Click me!
    </button>
  );
}

// Example 2

function Button() {
  const doStuff = () => {
    console.log("Do stuff.");
    console.log("Do more stuff.");
    console.log("Do EVEN MORE stuff!");
  };

  // NOTE: The function reference is passed instead of called (i.e. doStuff is passed, not doStuff() ).
  return <button onClick={doStuff}>Click me!</button>;
}
```

### Using the Event Parameter in Callbacks

* In React, the main event handlers we'll play with are `onClick`, `onChange`, and `onSubmit`.
  * Those will be triggered when a `click`, `submit`, or `change` event happens in the browser.
* When any of these events occur, an `event` object is automatically passed to the function that is invoked.
  * You may not necessarily use the event object, but it does have a lot of useful information.

```javascript
// Example where the x and y screen coordinates are printed to the console when a <div> is clicked.

function MyClickableDiv() {
  return (
    <div onClick={event => {
      console.log(`The mouse coordinates of this click event are: x: ${event.screenX} and y: ${event.screenY}`);
      }}
    >
    </div>
  );
}

// NOTE: The parameter that is automatically passed to the function when there is an event is often named 'event', though it is also very common for developers to simply name it 'e'.
```
