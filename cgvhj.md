# Project Name Documentation

## Table of Contents

- [Project Name Documentation](#project-name-documentation)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Folder Structure](#folder-structure)
  - [Naming Conventions](#naming-conventions)
  - [Imports](#imports)
    - [Library Imports](#library-imports)
    - [Absolute Imports](#absolute-imports)
    - [Relative Imports](#relative-imports)
  - [Coding Style Guide](#coding-style-guide)
    - [Idiomatic Style Manifesto](#idiomatic-style-manifesto)
    - [Whitespace](#whitespace)
    - [Beautiful Syntax](#beautiful-syntax)
      - [A. Parens, Braces, Linebreaks](#a-parens-braces-linebreaks)
      - [B. Assignments, Declarations, Functions (Named, Expression, Constructor)](#b-assignments-declarations-functions-named-expression-constructor)
      - [C. Exceptions, Slight Deviations](#c-exceptions-slight-deviations)
      - [D. Consistency Always Wins](#d-consistency-always-wins)
    - [Quotes](#quotes)
    - [End of Lines and Empty Lines](#end-of-lines-and-empty-lines)
    - [Type Checking (Courtesy jQuery Core Style Guidelines)](#type-checking-courtesy-jquery-core-style-guidelines)
      - [A. Actual Types](#a-actual-types)
      - [B. Coerced Types](#b-coerced-types)
      - [Common Cases](#common-cases)
      - [String and Number Comparison](#string-and-number-comparison)
      - [Array IndexOf Coercion](#array-indexof-coercion)
      - [Integer Coercion](#integer-coercion)
    - [Conditional Evaluation](#conditional-evaluation)
      - [A. Array Length and Empty Checks](#a-array-length-and-empty-checks)
      - [B. Type Coercion and Evaluation Notes](#b-type-coercion-and-evaluation-notes)
    - [Booleans, Truthies](#booleans-truthies)

## Introduction

Welcome to the documentation for our project! This document serves as a style guide and coding standard to ensure code consistency, readability, and maintainability.

## Folder Structure

Our project follows a well-organized folder structure to maintain clarity and simplicity. Here's an overview:

```plaintext
project-root/
  ├── src/
  │   ├── components/
  │   │   ├── MyComponent/
  │   │   │   ├── MyComponent.js
  │   │   │   ├── MyComponentStyles.css
  │   │   │   └── ...
  │   ├── utils/
  │   │   ├── utilityFunction.js
  │   │   └── HelperFunction.js
  │   ├── services/
  │   │   └── ApiService.js
  │   └── ...
  ├── data/
  │   └── data.json
  ├── assets/
  │   └── image.png
  ├── README.md
  ├── package.json
  └── ...
```

## Naming Conventions

- **PascalCase**: Use PascalCase for component names. For example: `MyComponent`.
- **CamelCase**: Use camelCase for utility or helper files and folder names.
- **Alphabetical Order**: Maintain alphabetical order for imports and file organization.

## Imports

### Library Imports

```jsx
// React Imports
import React from 'react';
import ReactDOM from 'react-dom';

// External Libraries
import axios from 'axios';
import { BrowserRouter as Router, Route } from 'react-router-dom';
import moment from 'moment';
```

### Absolute Imports

```jsx
// Custom or Absolute Imports
import MyComponent from 'components/MyComponent';
import utilityFunction from 'utils/utilityFunction';
import ApiService from 'services/ApiService';
import HelperFunction from 'utils/HelperFunction';
```

### Relative Imports

```jsx
// Internal Components
import Header from './Header';
import Footer from '../Footer';

// Utility Functions
import { formatDate } from './utils/dateUtils';
import { calculateTotal } from './utils/mathUtils';

// Styles or CSS for Specific Component
import './MyComponentStyles.css';

// JSON Data or Assets
import jsonData from '../data/data.json';
import image from '../assets/image.png';
```

## Coding Style Guide

### Idiomatic Style Manifesto

Follow the idiomatic style manifesto for modern JavaScript development. Consistency is key, and this guide serves as a commitment to code style consistency, readability, and maintainability.

### Whitespace

- Never mix spaces and tabs.
- Choose between soft indents (spaces) or real tabs at the beginning of the project.
- Set editor's indent size to two characters for readability.
- Use Editorconfig when possible.

### Beautiful Syntax

#### A. Parens, Braces, Linebreaks

```jsx
// Examples of really cramped syntax

if(condition) doSomething();

while(condition) iterating++;

for(var i=0;i<100;i++) someIterativeFn();

// Use whitespace to promote readability

if (condition) {
  // statements
}

while (condition) {
  // statements
}

for (var i = 0; i < 100; i++) {
  // statements
}

// Even better:

var i,
  length = 100;

for (i = 0; i < length; i++) {
  // statements
}

// Or...

var i = 0,
  length = 100;

for (; i < length; i++) {
  // statements
}

var prop;

for (prop in object) {
  // statements
}

if (true) {
  // statements
} else {
  // statements
}
```

#### B. Assignments, Declarations, Functions (Named, Expression, Constructor)

```jsx
// Variables
var foo = "bar",
  num = 1,
  undef;

// Literal notations:
var array = [],
  object = {};

// Using only one `var` per scope (function) or one `var` for each variable,
// promotes readability and keeps your declaration list free of clutter.
// Using one `var` per variable you can take more control of your versions
// and makes it easier to reorder the lines.
// One `var` per scope makes it easier to detect undeclared variables
// that may become implied globals.
// Choose better for your project and never mix them.

// Bad
var foo = "",
  bar = "";
var qux;

// Good
var foo = "";
var bar = "";
var qux;

// or..
var foo = "",
  bar = "",
  qux;

// or..
var // Comment on these
foo = "",
bar = "",
quux;

// var statements should always be in the beginning of their respective scope (function).

// Bad
function foo() {

  // some statements here

  var bar = "",
    qux;
}

// Good
function foo() {
  var bar = "",
    qux;

  // all statements after the variables declarations.
}

// const and let, from ECMAScript 6, should likewise be at the top of their scope (block).

// Bad
function foo() {
  let foo,
    bar;
  if (condition) {
    bar = "";
    // statements
  }
}
// Good
function foo() {
  let foo;
  if (condition) {
    let bar = "";
    // statements
  }
}

// Named Function Declaration
function foo( arg1, argN ) {

}

// Usage
foo( arg1, argN );

// Named Function Declaration
function square( number ) {
  return number * number;
}

// Usage
square( 10 );

// Function Expression
var square = function( number ) {
  // Return something valuable and relevant
  return number * number;
};

// Function Expression with Identifier
// This preferred form has the added value of being
// able to call itself and have an identity in stack traces:
var factorial = function factorial( number ) {
  if (number < 2) {
    return

 1;
  }

  return number * factorial( number - 1 );
};

// Constructor Declaration
function FooBar( options ) {

  this.options = options;
}

// Usage
var fooBar = new FooBar({ a: "alpha" });

fooBar.options;
// { a: "alpha" }
```

#### C. Exceptions, Slight Deviations

```jsx
// Functions with callbacks
foo(function() {
  // Note there is no extra space between the first paren
  // of the executing function call and the word "function"
});

// Function accepting an array, no space
foo([ "alpha", "beta" ]);

// Function accepting an object, no space
foo({
  a: "alpha",
  b: "beta"
});

// Single argument string literal, no space
foo("bar");

// Expression parens, no space
if (!("foo" in obj)) {
  obj = (obj.bar || defaults).baz;
}
```

#### D. Consistency Always Wins

```jsx
if (condition) {
  // statements
}

while (condition) {
  // statements
}

for (var i = 0; i < 100; i++) {
  // statements
}

if (true) {
  // statements
} else {
  // statements
}
```

### Quotes

Whether you prefer single or double quotes, choose one style and stick with it. Never mix quotes in the same project for consistency.

### End of Lines and Empty Lines

Whitespace can ruin diffs and make changesets impossible to read. Incorporate a pre-commit hook that removes end-of-line whitespace and blanks spaces on empty lines automatically.

### Type Checking (Courtesy jQuery Core Style Guidelines)

#### A. Actual Types

- String: `typeof variable === "string"`
- Number: `typeof variable === "number"`
- Boolean: `typeof variable === "boolean"`
- Object: `typeof variable === "object"`
- Array: `Array.isArray( arrayLikeObject )` (wherever possible)
- Node: `elem.nodeType === 1`
- null: `variable === null`
- null or undefined: `variable == null`
- undefined: `variable === undefined`
- Global Variables: `typeof variable === "undefined"`
- Local Variables: `variable === undefined`
- Properties:
  - `object.prop === undefined`
  - `object.hasOwnProperty( prop )`
  - `"prop" in object`

#### B. Coerced Types

Consider the implications of the following:

```jsx
// `foo` has been declared with the value `0` and its type is `number`
var foo = 0;

// Somewhere later in your code, you need to update `foo`
// with a new value derived from an input element

foo = document.getElementById("foo-input").value;

// If you were to test `typeof foo` now, the result would be `string`
// This means that if you had logic that tested `foo` like:

if (foo === 1) {
  importantTask();
}

// `importantTask()` would never be evaluated, even though `foo` has a value of "1"
```

Here are some common cases along with coercions:

#### Common Cases

```jsx
var number = 1,
  string = "1",
  bool = false;

number; // 1
number + ""; // "1"
string; // "1"
+string; // 1
+string++; // 1
string; // 2
bool; // false
+bool; // 0
bool + ""; // "false"
```

#### String and Number Comparison

```jsx
var string = "1",
  number = 1,
  bool = true;

string === number; // false
string === number + ""; // true
+string === number; // true
bool === number; // false
+bool === number; // true
bool === string; // false
bool === !!string; // true
```

#### Array IndexOf Coercion

```jsx
var array = [ "a", "b", "c" ];

!!~array.indexOf("a"); // true
!!~array.indexOf("b"); // true
!!~array.indexOf("c"); // true
!!~array.indexOf("d"); // false

// Prefer the obvious approach of comparing the returned value of
// indexOf, like:

if (array.indexOf("a") >= 0) {
  // ...
}
```

#### Integer Coercion

```jsx
var num = 2.5;

parseInt(num, 10); // Same as ~~num or num >> 0 or num >>> 0; All result in 2

var neg = -2.5;

parseInt(neg, 10); // Same as ~~neg or neg >> 0; Result in -2, neg >>> 0 will result in 4294967294
```

### Conditional Evaluation

#### A. Array Length and Empty Checks

```jsx
// When only evaluating that an array has length,
// instead of this:
if (array.length > 0) ...

// ...evaluate truthiness, like this:
if (array.length) ...

// When only evaluating that an array is empty,
// instead of this:
if (array.length === 0) ...

// ...evaluate truthiness, like this:
if (!array.length) ...

// When only evaluating that a string is not empty,
// instead of this:
if (string !== "") ...

// ...evaluate truthiness, like this:
if (string) ...

// When only evaluating that a string _is_ empty,
// instead of this:
if (string === "") ...

// ...evaluate falsy-ness, like this:
if (!string) ...

// When only evaluating that a reference is true,
// instead of this:
if (foo === true) ...

// ...evaluate like you mean it, take advantage of built in capabilities:
if (foo) ...

// When evaluating that a reference is false,
// instead of this:
if (foo === false) ...

// ...use negation to coerce a true evaluation
if (!foo) ...

// ...Be careful, this will also match: 0, "", null, undefined, NaN
// If you _MUST_ test for a boolean false, then use
if (foo === false) ...

// When only evaluating a ref that might be null or undefined, but NOT false, "" or 0,
// instead of this:
if (foo === null || foo === undefined) ...

// ...take advantage of == type coercion, like this:
if (foo == null) ...

// Remember, using == will match a `null` to BOTH `null` and `undefined`
// but not `false`, "" or 0
null == undefined
```

#### B. Type Coercion and Evaluation Notes

- Prefer `===` over `==` (unless the case requires loose type evaluation)

```jsx
// === does not coerce type, which means that:

"1" === 1; // false

// == does coerce type, which means that:

"1" == 1; // true
```

### Booleans, Truthies