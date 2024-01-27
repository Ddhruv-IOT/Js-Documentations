# Project Name Documentation

## Table of Contents

- [Project Name Documentation](#project-name-documentation)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
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
      - [Conditional Evaluation](#conditional-evaluation)
    - [Practical Style](#practical-style)
      - [A Practical Module](#a-practical-module)
      - [A Practical Constructor](#a-practical-constructor)
    - [Miscellaneous](#miscellaneous)
      - [A. Switch Statements (Continued)](#a-switch-statements-continued)
      - [Example of an Unfavorable Switch Statement](#example-of-an-unfavorable-switch-statement)
      - [Alternate Approach using an Object to Store "Cases"](#alternate-approach-using-an-object-to-store-cases)
    - [B. Early Returns](#b-early-returns)
      - [Example of Late Return](#example-of-late-return)
      - [Example of Early Return](#example-of-early-return)
    - [Native \& Host Objects](#native--host-objects)
    - [Comments](#comments)
    - [One Language Code](#one-language-code)
    - [Appendix](#appendix)
  - [Contributing](#contributing)
  - [License](#license)

## Introduction

Welcome to the documentation for our project! This document serves as a style guide and coding standard to ensure code consistency, readability, and maintainability.

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

Consider the implications of the following...

Given this HTML:

```html
<input type="text" id="foo-input" value="1">
```

```javascript
// 3.B.1.1

// `foo` has been declared with the value `0` and its type is `number`
var foo = 0;

// typeof foo;
// "number"
...

// Somewhere later in your code, you need to update `foo`
// with a new value derived from an input element

foo = document.getElementById("foo-input").value;

// If you were to test `typeof foo` now, the result would be `string`
// This means that if you had logic that tested `foo` like:

if ( foo === 1 ) {

  importantTask();

}

// `importantTask()` would never be evaluated, even though `foo` has a value of "1"


// 3.B.1.2

// You can preempt issues by using smart coercion with unary + or - operators:

foo = +document.getElementById("foo-input").value;
//    ^ unary + operator will convert its right side operand to a number

// typeof foo;
// "number"

if ( foo === 1 ) {

  importantTask();

}

// `importantTask()` will be called
```

Here are some common cases along with coercions:

```javascript
// 3.B.2.1

var number = 1,
  string = "1",
  bool = false;

number;
// 1

number + "";
// "1"

string;
// "1"

+string;
// 1

+string++;
// 1

string;
// 2

bool;
// false

+bool;
// 0

bool + "";
// "false"
// 3.B.2.2

var number = 1,
  string = "1",
  bool = true;

string === number;
// false

string === number + "";
// true

+string === number;
// true

bool === number;
// false

+bool === number;
// true

bool === string;
// false

bool === !!string;
// true
// 3.B.2.3

var array = [ "a", "b", "c" ];

!!~array.indexOf("a");
// true

!!~array.indexOf("b");
// true

!!~array.indexOf("c");
// true

!!~array.indexOf("d");
// false

// Note that the above should be considered "unnecessarily clever"
// Prefer the obvious approach of comparing the returned value of
// indexOf, like:

if ( array.indexOf( "a" ) >= 0 ) {
  // ...
}
// 3.B.2.4


var num = 2.5;

parseInt( num, 10 );

// is the same as...

~~num;

num >> 0;

num >>> 0;

// All result in 2


// Keep in mind however, that negative numbers will be treated differently...

var neg = -2.5;

parseInt( neg, 10 );

// is the same as...

~~neg;

neg >> 0;

// All result in -2
// However...

neg >>> 0;

// Will result in 4294967294
```

#### Conditional Evaluation

```javascript
// 4.1.1
// When only evaluating that an array has length,
// instead of this:
if ( array.length > 0 ) ...

// ...evaluate truthiness, like this:
if ( array.length ) ...


// 4.1.2
// When only evaluating that an array is empty,
// instead of this:
if ( array.length === 0 ) ...

// ...evaluate truthiness, like this:
if ( !array.length ) ...


// 4.1.3
// When only evaluating that a string is not empty,
// instead of this:
if ( string !== "" ) ...

// ...evaluate truthiness, like this:
if ( string ) ...


// 4.1.4
// When only evaluating that a string _is_ empty,
// instead of this:
if ( string === "" ) ...

// ...evaluate falsy-ness, like this:
if ( !string ) ...


// 4.1.5
// When only evaluating that a reference is true,
// instead of this:
if ( foo === true ) ...

// ...evaluate like you mean it, take advantage of built in capabilities:
if ( foo ) ...


// 4.1.6
// When evaluating that a reference is false,
// instead of this:
if ( foo === false ) ...

// ...use negation to coerce a true evaluation
if ( !foo ) ...

// ...Be careful, this will also match: 0, "", null, undefined, NaN
// If you _MUST_ test for a boolean false, then use
if ( foo === false ) ...


// 4.1.7
// When only evaluating a ref that might be null or undefined, but NOT false, "" or 0,
// instead of this:
if ( foo === null || foo === undefined ) ...

// ...take advantage of == type coercion, like this:
if ( foo == null ) ...

// Remember, using == will match a `null` to BOTH `null` and `undefined`
// but not `false`, "" or 0
null == undefined
ALWAYS evaluate for the best, most accurate result - the above is a guideline, not a dogma.

// 4.2.1
// Type coercion and evaluation notes

// Prefer `===` over `==` (unless the case requires loose type evaluation)

// === does not coerce type, which means that:

"1" === 1;
// false

// == does coerce type, which means that:

"1" == 1;
// true


// 4.2.2
// Booleans, Truthies & Falsies

// Booleans:
true, false

// Truthy:
"foo", 1

// Falsy:
"", 0, null, undefined, NaN, void 0
```

### Practical Style

#### A Practical Module

```javascript
// 5.1.1
(function( global ) {
  var Module = (function() {

    var data = "secret";

    return {
      // This is some boolean property
      bool: true,
      // Some string value
      string: "a string",
      // An array property
      array: [ 1, 2, 3, 4 ],
      // An object property
      object: {
        lang: "en-Us"
      },
      getData: function() {
        // get the current value of `data`
        return data;
      },
      setData: function( value ) {
        // set the value of `data` and return it
        return ( data = value );
      }
    };
  })();

  // Other things might happen here

  // expose our module to the global object
  global.Module = Module;

})( this );
```

#### A Practical Constructor

```javascript
// 5.2.1
(function( global ) {

  function Ctor( foo ) {

    this.foo = foo;

    return this;
  }

  Ctor.prototype.getFoo = function() {
    return this.foo;
  };

  Ctor.prototype.set

  ### C. Using `thisArg` (Continued)

#### Example using `Array.prototype.forEach` with `thisArg`

```javascript
// 6.C.1
var obj;

obj = { f: "foo", b: "bar", q: "qux" };

Object.keys(obj).forEach(function (key) {

  // |this| now refers to `obj`

  console.log(this[key]);

}, obj); // <-- the last arg is `thisArg`
```

`thisArg` can be used with `Array.prototype.every`, `Array.prototype.forEach`, `Array.prototype.some`, `Array.prototype.map`, `Array.prototype.filter`.

### Miscellaneous

#### A. Switch Statements (Continued)

Using `switch` should be avoided, as modern method tracing will blacklist functions with switch statements. However, there seems to be drastic improvements to the execution of switch statements in the latest releases of Firefox and Chrome ([performance test](http://jsperf.com/switch-vs-object-literal-vs-module)). Notable improvements can be witnessed [here](https://github.com/petkaantonov/bluebird/wiki/Optimization-killers#3-managing-arguments), especially for specific use cases.

#### Example of an Unfavorable Switch Statement

```javascript
// 7.A.1.1
// An example switch statement

switch (foo) {
  case "alpha":
    alpha();
    break;
  case "beta":
    beta();
    break;
  default:
    // something to default to
    break;
}
```

#### Alternate Approach using an Object to Store "Cases"

```javascript
// 7.A.1.2
// An alternate approach that supports composability and reusability is to
// use an object to store "cases" and a function to delegate:

var cases, delegator;

// Example returns for illustration only.
cases = {
  alpha: function () {
    // statements
    // a return
    return ["Alpha", arguments.length];
  },
  beta: function () {
    // statements
    // a return
    return ["Beta", arguments.length];
  },
  _default: function () {
    // statements
    // a return
    return ["Default", arguments.length];
  }
};

delegator = function () {
  var args, key, delegate;

  // Transform arguments list into an array
  args = [].slice.call(arguments);

  // shift the case key from the arguments
  key = args.shift();

  // Assign the default case handler
  delegate = cases._default;

  // Derive the method to delegate operation to
  if (cases.hasOwnProperty(key)) {
    delegate = cases[key];
  }

  // The scope arg could be set to something specific,
  // in this case, |null| will suffice
  return delegate.apply(null, args);
};

// 7.A.1.3
// Put the API in 7.A.1.2 to work:

delegator("alpha", 1, 2, 3, 4, 5);
// [ "Alpha", 5 ]

// Of course, the `case` key argument could easily be based
// on some other arbitrary condition.

var caseKey, someUserInput;

// Possibly some kind of form input?
someUserInput = 9;

if (someUserInput > 10) {
  caseKey = "alpha";
} else {
  caseKey = "beta";
}

// or...

caseKey = someUserInput > 10 ? "alpha" : "beta";

// And then...

delegator(caseKey, someUserInput);
// [ "Beta", 1 ]

// And of course...

delegator();
// [ "Default", 0 ]
```

### B. Early Returns

Early returns promote code readability with negligible performance differences.

#### Example of Late Return

```javascript
// 7.B.1.1
// Bad:
function returnLate(foo) {
  var ret;

  if (foo) {
    ret = "foo";
  } else {
    ret = "quux";
  }
  return ret;
}
```

#### Example of Early Return

```javascript
// Good:
function returnEarly(foo) {
  if (foo) {
    return "foo";
  }
  return "quux";
}
```

### Native & Host Objects

The basic principle here is: **Don't do stupid shit and everything will be ok.** To reinforce this concept, please watch the following presentation: ["Everything is Permitted: Extending Built-ins" by Andrew Dupont (JSConf2011, Portland, Oregon)](https://www.youtube.com/watch?v=xL3xCO7CLNM).

### Comments

- Single line above the code that is subject.
- Multiline comments are good.
- End of line comments are prohibited!
- JSDoc style is good but requires a significant time investment.

### One Language Code

Programs should be written in one language, whatever that language may be, as dictated by the maintainer or maintainers.

### Appendix

- Comma First. Any project that cites this document as its base style guide will not accept comma-first code formatting, unless explicitly specified otherwise by that project's author.

- Use Standard for JavaScript style guide, linter, and formatter [Standard-JS](https://github.com/standard/standard)

## Contributing

We welcome contributions! If you have any questions or suggestions, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
