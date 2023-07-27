---
layout: post
title: "Hoisting In JavaScript"
date: 2023-07-19 22:30:11 +0200
categories: javascript hoisting
---

## Before going into more details...

### The Javascript Interpreter

Wikipedia states:

> _"An interpreter is a computer program that directly executes instructions written in a programming or scripting language without requiring them previously to have been compiled into a machine language program. It translates one Statement at a time."_

#### Phases

![The Javascript interpreter phases](https://cdn.hashnode.com/res/hashnode/image/upload/v1591086993233/s-2Gy4x3s.gif?auto=format,compress&gif-q=60&format=webm)

##### Tokenizing

Breaking up a source code string into meaningful chunks called, **Tokens**. For example, the source code var age = 7; can be tokenize as, var, age, =, 7 and, ;.

##### Parsing

Parsing is a methodology to take the array of Tokens as input and turn it into a tree of nested elements understood by the grammar of the programming language. This tree is called Abstract Syntax Tree (AST).

##### Code Generation

In this phase, the **A**bstract **S**yntax **T**ree is used as input, and an executable byte-code is generated that is understood by the environment(or platform) where the executable code will be running. The executable byte-code is then refined/converted even further by the optimizing JIT (Just-In-Time) compiler.

### Scopes in Javascript

In JavaScript, scope refers to the accessibility and visibility of variables, functions, and objects within different parts of your code during runtime. Understanding scopes is crucial for writing clean, bug-free, and maintainable JavaScript code.

There are two main types of scope in JavaScript:

#### Global Scope

Variables and functions declared outside of any function or block have global scope. They are accessible from anywhere in your code, including within functions.

```javascript
var globalVar = 10;

function globalFunction() {
  console.log(globalVar); // Output: 10
}

globalFunction();
```

In this example, `globalVar` and `globalFunction` are accessible from anywhere in the code.

#### Local Scope

Variables and functions declared inside a function or block have local scope. They are only accessible within the function or block where they are defined.

```javascript
function localFunction() {
  var localVar = 20;
  console.log(localVar); // Output: 20
}

localFunction();
// console.log(localVar); // This would result in an error since localVar is not accessible here
```

In this example, `localVar` is only accessible within the `localFunction` and cannot be accessed from outside.

#### Nested Scopes

Scopes can also be nested, meaning one scope can be contained within another. Inner scopes have access to variables from their parent (outer) scopes, but not vice versa.

```javascript
var outerVar = 30;

function outerFunction() {
  var innerVar = 40;

  function innerFunction() {
    console.log(outerVar); // Output: 30
    console.log(innerVar); // Output: 40
  }

  innerFunction();
}

outerFunction();
// console.log(innerVar); // This would result in an error since innerVar is not accessible here
```

In this example, `innerFunction` has access to both `outerVar` and `innerVar`, but `outerFunction` cannot access `innerVar`.

#### Block Scope (ES6 and later)

With the introduction of `let` and `const` in ES6, you can also create block-scoped variables using the `let` and `const` keywords within blocks (e.g., `if`, `for`, `while`).

```javascript
if (true) {
  var x = 50; // Function-scoped
  let y = 60; // Block-scoped
  const z = 70; // Block-scoped
}

console.log(x); // Output: 50
// console.log(y); // This would result in an error since y is block-scoped
// console.log(z); // This would result in an error since z is block-scoped
```

In this example, `x` is function-scoped and accessible outside the `if` block, while `y` and `z` are block-scoped and cannot be accessed outside the `if` block.

Understanding scopes is vital to prevent unintended variable clashes and to write efficient and organized JavaScript code. It enables you to control the visibility and lifetime of variables and functions within your programs.

## What is hoisting ?

[MDN Web Doc](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) defines hoisting in javascript as _the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code_

Hoisting is what allows this code to work:

```typescript
sum(1, 1);

function sum(a: number, b: number): number {
  return a + b;
}
```

### ChatGPT's description

Hoisting in JavaScript is a concept that can sometimes lead to confusion among programmers. It refers to how JavaScript behaves when it encounters variable and function declarations during the compilation phase. To help you understand hoisting visually, let's explore some code snippets.

#### Hoisting with Variable Declarations

```javascript
console.log(x); // Output: undefined
var x = 5;
console.log(x); // Output: 5
```

In this example, the variable `x` is declared and initialized with the value `5`. However, before the declaration, we try to log the value of `x`, which results in `undefined`. This is because variable declarations are hoisted to the top of their scope during compilation but not their values. So, the code is interpreted like this:

```javascript
var x; // The declaration is hoisted
console.log(x); // Output: undefined
x = 5; // The assignment stays in place
console.log(x); // Output: 5
```

#### Hoisting with Function Declarations

```javascript
foo(); // Output: "Hello, I'm foo!"

function foo() {
  console.log("Hello, I'm foo!");
}
```

In this example, the function `foo` is called before its actual declaration in the code. Surprisingly, it works without any errors. This is because function declarations are also hoisted to the top of their scope during compilation, allowing the code to be interpreted like this:

```javascript
function foo() {
  console.log("Hello, I'm foo!");
}

foo(); // Output: "Hello, I'm foo!"
```

#### Hoisting with Variable and Function Declarations

```javascript
var y = 10;

function bar() {
  console.log(y); // Output: undefined
  var y = 20;
}

bar();
```

In this example, we have a variable `y` and a function `bar`. Inside `bar`, we try to log the value of `y` before its actual declaration and assignment within the function. Similar to the previous examples, variable declarations within the function are hoisted to the top of their scope, resulting in the following interpretation:

```javascript
function bar() {
  var y; // The declaration is hoisted
  console.log(y); // Output: undefined
  y = 20; // The assignment stays in place
}

var y = 10;
bar();
```

#### Visual Representation

Imagine hoisting as if declarations are physically moved to the top of their respective scopes during the compilation phase, like this:

```javascript
// Code during compilation phase with hoisting:

var x; // Variable declaration is hoisted
console.log(x); // Output: undefined
x = 5; // The assignment stays in place
console.log(x); // Output: 5

function foo() {
  console.log("Hello, I'm foo!");
}

foo(); // Output: "Hello, I'm foo!"

// ...

var y = 10;

function bar() {
  var y; // Variable declaration is hoisted
  console.log(y); // Output: undefined
  y = 20; // The assignment stays in place
}

bar();
```

Keep in mind that hoisting can lead to unexpected behavior if not understood properly. Always declare your variables at the beginning of their scope and avoid relying on hoisting to ensure clearer and more maintainable code.