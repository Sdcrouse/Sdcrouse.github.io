---
layout: post
title:      "The Importance of Scope, Hoisting, and the JavaScript Engine, Part 2"
date:       2020-07-09 23:04:02 -0400
permalink:  the_importance_of_scope_hoisting_and_the_javascript_engine_part_2
---


In my previous blog post, I discussed how scope works in JavaScript. I explored a couple of key scope-related concepts, and I briefly touched upon closures. Here, I will conclude my discussion of scope by describing a couple of "exceptions" to the concepts that I previously wrote about. Then, I will describe hoisting and how it is closely connected with the JavaScript engine's compilation and execution phases. An understanding of how scope, hoisting, and the JavaScript engine work, is critical to becoming a good JavaScript developer; a lot of bugs can be avoided or corrected, especially when dealing with legacy code.
## "Exceptions" to the Rules
Unfortunately (or fortunately, depending on your point of view), there are a couple of "exceptions" to the scope-related concepts that I described in the previous post, and they are often encountered in legacy (pre-ES6/ECMA2015) code. 

### Exception 1
The first exception is global variables. If you define a variable without the `let`, `const`, or `var` keywords, they are available (and modifiable) *everywhere.* In other words, this code technically works:
```
function anotherTest() {
  testVar = 123;
}

anotherTest(); 

console.log("This will not generate a ReferenceError:");
console.log(testVar);

//=> This will not generate a ReferenceError:
//=> 123
```

This is generally a *very bad idea*. Whenever possible, you want to limit the scope of your variables to where they are needed; otherwise, you might accidentally change a variable's value in an unexpected place. That would be hard to debug, as there might be multiple places that could have modified that variable.

> **Side Note:** For this example to work, `anotherTest` needed to be invoked before the `console.log` statements. Otherwise, I would in fact have gotten a ReferenceError.

### Exception 2
A second scope-related exception is block scope. Whether or not a variable can be scoped to a block depends on the keyword. `let` and `const` allow for block scope, but `var` does not. This is shown below:
```
  if (true) {
	  const blockScoped = 123;
		var notBlockScoped = "abc";
  }
	
	console.log("I can access the notBlockScoped variable:");
	console.log(notBlockScoped);
	
	console.log("But I can't access blockScoped:");
	console.log(blockScoped);
	
	//=> I can access the notBlockScoped variable:
  //=> abc
  //=> But I can't access blockScoped:
  //=> Uncaught ReferenceError: blockScoped is not defined
```

> **Side note:** This is one of many reasons why the usage of `var` is not recommended nowadays. However, it often shows up in legacy code, as that was the only way to declare a variable before ECMA2015 introduced `const` and `let`.

## A Quick Detour into the JavaScript Engine
Before I discuss hoisting, I need to mention the JavaScript engine. When it runs the code, it goes through two phases: compilation and execution.

In the compilation phase, the JavaScript engine finds all of the variable and function declarations, assigns memory for each of them, and sets up references to them. It also sets up the global scope and function scopes, and it creates the scope chains by assigning references to each scope's parent/outer scope. It does *not* assign any values to variables.

In the execution phase, JavaScript runs over the code a second time, setting values to variables and calling functions. It ignores all of the `const`, `var`, `function`, etc. declarations. This is where it generates `ReferenceErrors` whenever it can't find a matching declared variable, or a function with a certain name, in the current scope and scope chain.

Here's a simple example: 
```
let abc = 123;

console.log(abc);
```

In the compilation phase, JavaScript sets aside some memory for a variable called `abc` and sets a reference to it. It does not assign it any value, so `abc` is `undefined` at this time. It also ignores the `console.log` statement.

In the execution phase, JavaScript reads the code in the way that we're used to seeing in Ruby: It sees the declared variable `abc` and assigns it a value of `123`. It then prints `123` in the console.

Knowing how the JavaScript engine works under the hood, with its separate compilation and execution phases, is the key to understanding hoisting.

## Hoisting
Hoisting is the ability to call functions and certain variables seemingly before they are declared. Even though they're written further down in the code, they seem to be "hoisted up" to the top of their scope.

### Variable Hoisting

Here's an example of how this works with variables:
```
function myTestFunction() {
  console.log(`The value of 'exampleVar' is ${exampleVar}.`);

  var exampleVar = 9876;
	
	console.log(`The value of 'exampleVar' is now ${exampleVar}.`);
}
```

What happens when we call `myTestFunction`? It looks like we'd get an error since the first `console.log` statement is trying to reference `exampleVar` before it gets defined. However, this is what gets displayed in the console:
```
myTestFunction()

The value of 'exampleVar' is undefined.
The value of 'exampleVar' is now 9876.
```

That looks pretty weird at first glance. But this is where it helps to remember how JavaScript's engine works. 

First, the engine's compilation phase stores memory for `myTestFunction`, sets a reference to that function, and sets up its scope. It then ignores the first `console.log` statement and sets aside memory for, and a reference to, `exampleVar`. It does not assign it a value, and it ignores the next `console.log` statement.

Then in the execution phase, the JavaScript engine goes into `myTestFunction` and executes the first `console.log` statement. It sees the reference to `exampleVar`, recognizes that it has been *declared* but not *defined* yet, and prints out `undefined` as its value. Then, the engine goes to the next line of code, ignores the `var` keyword, and sets `exampleVar`'s value to 9876. Finally, it executes the second `console.log` statement with that new value of `exampleVar`. The code above is effectively equivalent to this:
```
function myTestFunction() {
  var exampleVar; // Undefined, initially
	
  console.log(`The value of 'exampleVar' is ${exampleVar}.`);

  exampleVar = 9876;
	
	console.log(`The value of 'exampleVar' is now ${exampleVar}.`);
}
```

This is what hoisting is. Because of the way JavaScript's engine goes through its compilation and execution phases, it's as though `exampleVar` has been "hoisted up" to the top of `myTestFunction`'s inner scope.

### Function Hoisting

Hoisting also happens with function declarations:
```
displayMessage();

//........... Additional Code ............

function displayMessage() {
  console.log("I get displayed even though displayMessage is called above its function declaration.");
}
```

If you try this out in console, the `console.log` statement inside of `displayMessage` will be displayed without any errors. Just like with variables, the `displayMessage` function appears to have been "hoisted up" to the top of its scope (the global scope, in this case).

### How to Limit Hoisting

This sort of thing has tripped up a lot of programmers in the past, which is one reason why it's important to know how hoisting works. This is especially true with legacy code. However, there are a couple of ways to prevent (or at least limit) hoisting. One good way is to declare all of your functions and variables as close to the top of your code as possible. That leads to fewer bugs, and it keeps your code more organized. Another, *highly recommended* way, is to use `let` and `const` instead of `var`. In addition to limiting scoping issues (as mentioned in the previous post), variables declared with `let` and `const` generate errors if you try to call them before assigning them values:
```
console.log(myTestA);
let myTestA = 'Lorem ipsum';
//=> Uncaught ReferenceError: myTestA is not defined

console.log(myTestB);
const myTestB = 'abc';
//=> Uncaught ReferenceError: Cannot access 'myTestB' before initialization
```

> **Special note about OOJS:** According to [the official documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#Hoisting), function declarations are hoisted, but class declarations are *not*. When programming with Object-Oriented JavaScript, be sure to declare your classes before calling them.

## Conclusion
As we have seen in this blog post and the one before it, it is important to understand how scope, hoisting, and the JavaScript engine all work. This can help us avoid a lot of potential errors - or at the very least correct the ones that exist - especially when dealing with legacy code. Just to summarize:

1. Scope is where a given set of functions and/or variables can be accessed. Function scope and global scope are examples of this.
2. Hoisting is how functions and variables declared with `var` can seemingly be accessed before they are defined. They are "hoisted" to the top of their scopes.
3. Hoisting is possible because of how the JavaScript engine works: It first sets aside memory and references to any declared functions and variables, and it sets up scopes. Then, it runs through the code a second time to assign values to variables, execute calls to functions, etc.
4. It is recommended that we use ES6 syntax (`let` and `const`) and declare our functions and variables at or near the top of our code whenever possible.

Thank you for reading over these blog posts! Stay safe out there, and happy coding.
