# 20221202 工作筆記

## React Hooks

> A Hook is a special function that lets you "hook into" React features. `useState` is a Hook that lets you add React state to function components.

If we need to add some to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function.

### useState

#### 1. Declaring a State Variable

> We declare a state variable called `count`,and set it to 0. React will remember its current value between re-renders, and provide the most recent one to our function. If we want to update the current `count`, we can call `setCount` function.

```javascript
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, serCount] = useState(0);
}
```

- `useState` declares a "state variable". and it is a new way to use the exact same capabilities that `this.state` provides in a class.

- The only argument to the `useState()` Hook is the **_initial state_**. Unlike with classes, **_the state doesn't have to be an object._** We pass `0` as initial state for our variable.

  > If we wanted to store two different values in state, we would call `useState()` twice.

- `useState` returns a pair of values: **_the current state and a function that updates it._** So the example statement is similar to `this.state.count` and `this.setState` in a class component.

#### 2. Reading State

> Use the variable directly.

```html
<p>You clicked { count } times</p>
```

#### 3. Updating State

> In a function component, we already have `setCount` and `count` as variables so we don't need `this`.

```html
<button onClick={ () => setCount(count+1)}>
  Click me
</button>
```

### useEffect(待補)

### useRef(待補)

### useMemo(待補)

### 參考文章

- [Using the State Hook](https://reactjs.org/docs/hooks-state.html)

---

## React global var settings

1. create a new file called `GlobalVar.js`, to define a constant `globalVar` and assign it a value.
   ```javascript
   #React
   const globalVar = "I am a Global Variable";
   export default globalVar;
   ```
2. Now it work as a global variable.

   ```javascript
   #React
   import globalVar from "./GlobalVar";

   export default function  App(){
    return(
      <div className="App">
        <h2>{ globalVar }</h2>
      </div>
     )
   }
   ```

### 參考文章

- [Global Variable in React](https://www.delftstack.com/howto/react/global-variable-in-react/)

---

## JavaScript

### 1. return statement's rules

- Every function in JavaScript returns `undefined` unless otherwise specified.
- The return statement ends function execution immediately.
- The return statement returns a value to the function caller.
- The return statement can also be used to interrupt or end a function.
- The return statement can alse interrupt a loop and stop execution midway through.
- The return statement can even return a function from within a function.([Closures](https://codeburst.io/understand-closures-in-javascript-d07852fa51e7))

### 2. Arrow function's return rules

#### No need the return statement :

- Single Expression Return

  ```javascript
  const breakfast = () => 'Cinnamon Toast Crunch';
  breakfast(); //'Cinnamon Toast Crunch'
  ```

  ```javascript
  const breakfast = () => 'Cinnamon Toast Crunch';
  breakfast(); //'Cinnamon Toast Crunch'
  ```

  ```javascript
  const lunch = () => 'Chipotle';
  lunch(); //'Chipotle'
  ```

- Object literals wrapped in {}

  Keep your code to a single line, or are adamant that you don't want to use the `return` statement.

  ```javascript
  const moreDessert = () => ({ dessert: 'Key Lime Pie' });
  moreDessert(); //{ dessert: "Key Lime Pie"}
  ```

#### Need the return statement :

- Function body wrapped in curly brackets require a return statement.

  ```javascript
  const dinner = () => {
    return 'Mac and Cheese';
  };
  dinner(); // "Mac and Cheese"

  const dinner = () => {
    'Mac and Cheese';
  };
  dinner(); // undefined
  ```

- Multiple line statement or expressions.
  Arrow funciton with curly brackets are the only way to get multiple statements or expressions inside the function body.

  ```javascript
  const drink = () => {
    const quantity = Math.floor(Math.random() * 10);
    return `I aim to drink ${quantity} glasses of water today.`;
  };
  drink(); // "I aim to drink ${quantity} glasses of water today."
  ```

### 3. Closure

What's closure ?

- A closure is a function that has access to the parent scope, even after the scope has closed.

- A closure is the combination of a function and the lexical environment within which that function was declared.

> It's important to note that every function in JavaScript has a closure. There's nothing you need to explicitly do to a function to get this to work. It just a part of JavaScript.

### 參考文章

- [JavaScript: What is the return statement?](https://codeburst.io/javascript-what-is-the-return-statement-97d8b11a1a0c)

- [Arrow Function => Return Rules](https://medium.com/@gracet37/arrow-function-return-rules-4bab63961b92)

- [Arrow function expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

- [Understand Closures in JavaScript](https://codeburst.io/understand-closures-in-javascript-d07852fa51e7)

---

### 下週可研究項目

1. [Debounce & Throttle ](https://medium.com/@alexian853/debounce-throttle-%E9%82%A3%E4%BA%9B%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC%E6%87%89%E8%A9%B2%E8%A6%81%E7%9F%A5%E9%81%93%E7%9A%84%E5%B0%8F%E4%BA%8B-%E4%B8%80-76a73a8cbc39)
