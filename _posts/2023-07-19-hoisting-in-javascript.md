---
layout: post
title: "Hoisting In JavaScript"
date: 2023-07-19 22:30:11 +0200
categories: javascript hoisting
---

## What is hoisting ?

[MDN Web Doc](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) defines hoisting in javascript as _the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code_

Hoisting is what allows this code to work:

```typescript
sum(1, 1);

function sum(a: number, b: number): number {
  return a + b;
}
```

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

<!-- > This is called function hoisting

The JavaScript interpreter hoists the entire function declaration to the top of the current scope and therefore it is accessible when the interpreter executes the code. -->
