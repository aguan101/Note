# 20221208 工作筆記

## JavaScript Excution Context

> The most important and fundamental concept to understanding the JavaScipt language is understanding Execution Context.

One strategy for writting software is to break our code up into separate pieces. Though these "pieces" have many different names( functions, modules, packages, etc ),they all exist for a single purpose - **_to break apart and manage the complexity in our applications._**
Can we use that same strategy,separating code into pieces, to manage the complexity of interpreting code just like we did in order to write it? Turns out we can and these "pieces" are called Execution Contexts.**_Just like functions/modules/packages/allow you to manage the complexity of writing code, Excution Contexts allow the JavaScript engine to manage the complexity of interpreting and running your code._**

### Global Excution Context

> The first Execution Context that gets created when the JavaScript engine runs your code.

Initially this Execution Context will consist of two things - a global object and a variable called `this`. `this` will reference the global object which will be `window` if you're running JavaScript in the browser or `global` if you're running it in a Node environment.

> Each Execution Context has two separate phases, a `Creation` phase and `Execution` phase and each phase has its own unique responsibilities.

- Global `Creation` phase

  1. Create a global object.
  2. Create a object called "`this`".
  3. Set up memory space for variables and functions.
  4. Assign variable declarations a default value of "undefined" while placing any function declarations in memory.

> Then once we enter the `Execution` phase, the JavaScript engine starts executing the code line by line and **_assigns the real values to the variables already living ing memory_**.

### Hoisting

> Assigning variable declarations a default value of `undefined` during the creation phase is called **_Hoisting_**.

提升不是真的在底層執行時被搬到程式碼的最前面，只是看起來很像而已。實際上會有這樣的結果只是因為在 Global Execution Context 中的 Creation 階段裡先將所有宣告的變數建立一個記憶體空間並賦予 undefined 的值。

```javascript
console.log('name: ', name); // name: undefined
console.log('handle: ', handle); // handle: undefined
console.log('getUser :', getUser); // getUser: ƒ getUser () {}

var name = 'Tyler';
var handle = '@tylermcginnis';

function getUser() {
  return {
    name: name,
    handle: handle,
  };
}
```

### Function Execution Context

> Created whenever a function is invoked.

We should only ever have one global object that's created durging the `Creation` phase of the Global Execution Context, not every time a function is invoked and the JavaScript engine creates a Functon Execution Context.

> In reality, the JavaScript engine creates what's called an "Execution Stack"( also known as the "Call Statck"). Anytime a function is invoked, a new Execution Context is created and added to the Execution Stack.

Whenever a function is finished running through both the `Creation` and `Execution` phase, **_it gets popped off the Execution Stack_**. Because JavaScript is **_single threaded_**( meaning only one task can be executed at a time).

When we invoke a function, a new Execution Context is created. During the `Creation` phase of a function Execution Context, the JavaScript engine creates a `this` object as well as an `arguments` object.

> If a function doesn't have any variables, the JavaScript engine doesn't need to set up any memory space or "hoist" any variable declarations.

### Scopes

> The current context of execution.

Variables created inside of a function are locally scoped. That means they can't be accessed once the function's Execution Context has been popped off the Excution Stack.

```javascript
function first() {
  var name = 'Jordyn';

  console.log(name);
}

function second() {
  var name = 'Jake';

  console.log(name);
}

console.log(name);
var name = 'Tyler';
first();
second();
console.log(name);
// undefined, Jordyn, Jake, Tyler
```

> Each new Execution Context as having its own unique variable environment. Even though there are other Execution Contexts that contain the varialbe `name`, **_the JavaScript engine will first look to the current Execution Context for that variable_**.

### Scope Chain

If the JavaScript engine can't find a variable local to the function's Execution Context, it'll look to the nearest parent Execution Context for that variable. This lookup chain will continue all the way until the engine reaches the Global Execution Context. In that case, if the Global Execution Context doesn't have the variable, it'll throw a Reference Error.

> This process of the JavaScript engine going one by one and checking each individual parent Execution Context if a variable doesn't exist in the local Execution Context is called the `Scope Chain`.

Any child Execution Context can reference any variables located in any of its parent Execution Context, but not vice versa.

### Closure

> A child function "closing" over the variable environment of its parent function is called `Closures`.

```javascript
var count = 0;

function makeAdder(x) {
  return function inner(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
count += add5(2);
```

Inside of that `Closure Scope` is the same variable environment that existed in the `makeAdder`Execution Context. This happened is because that we hava a function nested inside of another function.

---

### 參考文章

- [The Ultimate Guide to Hoisting, Scopes, and Closures in JavaScript](https://ui.dev/ultimate-guide-to-execution-contexts-hoisting-scopes-and-closures-in-javascript?spm=ata.13261165.0.0.2d8e16798YR8lw)

---

### 下週可研究項目

- [ Understanding the "this" keyword, call, apply, and bind in JavaScript ](https://ui.dev/this-keyword-call-apply-bind-javascript)
