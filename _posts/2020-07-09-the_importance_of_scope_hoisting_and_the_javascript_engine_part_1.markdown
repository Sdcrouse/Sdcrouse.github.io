---
layout: post
title:      "The Importance of Scope, Hoisting, and the JavaScript Engine, Part 1"
date:       2020-07-09 22:36:13 -0400
permalink:  the_importance_of_scope_hoisting_and_the_javascript_engine_part_1
---


Scope and hoisting are essential concepts to understand when programming in JavaScript. Scope is where a given set of functions and variables can be accessed.  Hoisting is what allows for functions and certain variables to be accessed and manipulated from the top of the current scope, even when they are defined/declared further down in that scope. In order to fully understand hoisting, one must also understand how JavaScript's engine works (i.e. what it does during the compilation phase and the execution phase, and the order that it runs through these phases). By knowing how all of this works together, one can avoid (or at least fix) a few commonly-encountered bugs in JavaScript code.

In this first part of the blog post, I will describe a few key scope-related concepts. In Part 2, I will point out a couple of "exceptions" to these concepts, and I will describe how hoisting and the JavaScript engine work.


## Scope
Let's say we have the following lines of code: 
```
let myNum = 123;

function testFunction () {
  const anotherNum = 456;
	
	console.log(`The value of anotherNum is ${anotherNum}.`);
	console.log(`The value of myNum (accessed from the inner scope of testFunction) is ${myNum}.`);
	
	myNum = 789;
}

console.log(`The value of myNum (accessed from the outer global scope) is ${myNum}.`);

testFunction();

console.log(`testFunction changed myNum to ${myNum}.`);
console.log(`The value of anotherNum (accessed from the outer global scope) is ${anotherNum}.`);
```

If we put that into our browser's console, we will see this output:
```
The value of myNum (accessed from the outer global scope) is 123.

The value of anotherNum is 456.

The value of myNum (accessed from the inner scope of testFunction) is 123.

testFunction changed myNum to 789.

Uncaught ReferenceError: anotherNum is not defined
```

The above output is possible in large part because of how scope works in JavaScript. Scope essentially answers this question: "Where can these variables and functions be accessed?" The code and output above demonstrate a few key concepts about scope in JavaScript.

### Scope Concept 1: Variables and Functions in the Same Scope

Functions, variables, expressions, etc. that are defined within the same scope, have access to each other. Look at this part of the code above:
```
let myNum = 123;

function testFunction () {...}

console.log(`The value of myNum (accessed from the outer global scope) is ${myNum}.`);

testFunction();
```
The last two lines of code are able to access the `myNum` variable and the `testFunction` function because they are in the *same scope* as `myNum` and `testFunction` (which is the global scope, in this case).

### Scope Concept 2: A Function's Inner Scope

Functions have their own inner scope; they can access variables and functions defined inside of them, but anything written outside of them *cannot*. Let's look at this part of the original code:
```
function testFunction () {
  const anotherNum = 456;
	
	console.log(`The value of anotherNum is ${anotherNum}.`);
	
	// The rest of the function
}

testFunction();
//=> The value of anotherNum is 456.

console.log(`The value of anotherNum (accessed from the outer global scope) is ${anotherNum}.`);
// => Uncaught ReferenceError: anotherNum is not defined
```

As demonstrated above, the `console.log` statement inside of `testFunction` is able to access `anotherNum` because they both have the same scope: the inner scope of `testFunction`. However, the `console.log` statement *outside* of `testFunction` generates an error because it does not have access to `anotherNum`, which is defined *inside* of `testFunction`.

This is getting complicated enough, but the original code and output demonstrate *yet another* concept about scope.

### Scope Concept 3: Scope Chain

Whenever a function is declared, the JavaScript engine sets up a *scope chain*. This chain allows functions (and anything inside of them) to not only access their *inner* scopes, but the *outer* scopes as well. Let's look at this portion of the original code, for a demonstration:
```
let myNum = 123;

function testFunction () {	
	console.log(`The value of myNum (accessed from the inner scope of testFunction) is ${myNum}.`);
	
	myNum = 789;
}

testFunction();
//=> The value of myNum (accessed from the inner scope of testFunction) is 123.

console.log(`testFunction changed myNum to ${myNum}.`);
//=> 
```

Because it had access to the global scope through the scope chain, `testFunction` was able to access and modify `myNum`. (Technically, it was only able to modify `myNum` because I used the `let` keyword; `var` would have worked as well, but `const` would have generated an error, since I would be attempting to change a constant value.)

On a related note, any functions and variables that are defined in the global scope (the outermost scope) are accessible *everywhere*. Since `myNum` was in the global scope, the `console.log` statements inside and outside of `testFunction` had access to it.

Also, if you define a function within a function, the scope chain allows for the inner function to access its inner scope, the outer function's scope, and the global scope. In other words, this code will work just fine:
```
const two = 2;

function outer() {
  const four = 4;
	
	function inner() {
	  const six = 6;
		
		console.log(`2 x 4 x 6 = ${two * four * six}`);
		console.log("See? Because of the scope chain, I have access to all three constants!");
	}
	
	inner();
}

outer();
//=> 2 x 4 x 6 = 48
//=> See? Because of the scope chain, I have access to all three constants!
```
## A Quick Note About Closures
There is still another scope-related concept called a *closure*. In summary, it is an inner function that gets returned by an outer function. Even though we have exited out of the outer function, the returned inner function still has access to the outer function's variables and scope. I would go into further detail about this, but that is beyond the scope (pun intended) of this blog post. For those who are curious, more information can be found here: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)

## Conclusion

This concludes Part 1 of my blog post. So far, I have covered a lot of scope-related concepts. In Part 2, I will discuss a couple of "exceptions" to these scope-related concepts. I will also describe hoisting and how the JavaScript engine works; as we will see, the JavaScript engine is key to understanding how hoisting is possible in the first place.
