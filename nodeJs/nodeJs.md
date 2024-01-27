# Node.js Coding Conventions Documentation

## Table of Contents

- [Node.js Coding Conventions Documentation](#nodejs-coding-conventions-documentation)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Folder Structure](#folder-structure)
  - [Basic Rules](#basic-rules)
  - [Naming Conventions](#naming-conventions)
  - [File Naming](#file-naming)
  - [Import Conventions](#import-conventions)
    - [Library Imports](#library-imports)
    - [Absolute Imports](#absolute-imports)
    - [Relative Imports](#relative-imports)
  - [Alignment](#alignment)
  - [Quotes](#quotes)
  - [Spacing](#spacing)
  - [Testing](#testing)
  - [Linting](#linting)
  - [Logging](#logging)
    - [1. Use a Logging Library](#1-use-a-logging-library)
    - [2. Log Levels](#2-log-levels)
    - [3. Include Contextual Information](#3-include-contextual-information)
    - [4. Log to Files or External Services](#4-log-to-files-or-external-services)
    - [5. Monitor Logs](#5-monitor-logs)
    - [Example Using Winston](#example-using-winston)
  - [Anti-Patterns](#anti-patterns)
    - [1. Callback Hell (Pyramid of Doom)](#1-callback-hell-pyramid-of-doom)
    - [2. Blocking the Event Loop](#2-blocking-the-event-loop)
    - [3. Global Variables](#3-global-variables)
    - [4. Overusing `console.log` for Debugging](#4-overusing-consolelog-for-debugging)
    - [5. Ignoring Error Handling](#5-ignoring-error-handling)
    - [6. Excessive Dependencies](#6-excessive-dependencies)
    - [7. Inefficient String Concatenation](#7-inefficient-string-concatenation)
    - [8. Not Scaling Your Application](#8-not-scaling-your-application)
    - [9. Ignoring Security Best Practices](#9-ignoring-security-best-practices)
  - [Best Practices](#best-practices)
  - [Contributing](#contributing)
  - [License](#license)

## Introduction

Welcome to the Node.js Coding Conventions documentation. This guide outlines the recommended coding practices and conventions to ensure consistency and readability in Node.js projects.

## Folder Structure

In a Node.js project, maintaining a well-organized folder structure is crucial for scalability and maintainability. Here's a suggested folder structure:

``` plaintext
.
├── config/        
│   ├── db.js
│   └── logger.js
├── constants/    
├── controllers/
├── logs/
│   ├── error.log
│   └── info.log
├── middlewares/
├── models/ (One model per file, and file should be named after model)
├── public/
│   ├── images/
│   ├── videos/
│   ├── files/
│   └── ...
├── routes/
│   ├── indexRoutes.js
│   └── ... other route files (one for each model recommended)
├── scripts/
├── test/
├── utils/
├── .git/
├── docker-comose.yaml
├── Dockerfile
├── package.json
├── Readme.md
├── server.js
├── .dockerignore
├── .env
├── .gitignore
└── .sample.env
```

## Basic Rules

Follow these basic rules to ensure code quality and consistency:

- Use meaningful variable and function names.
- Keep functions short and focused.
- Document your code with comments where necessary.

## Naming Conventions

Consistent naming conventions enhance code readability. Follow these guidelines:

- Use camelCase for variables and functions (e.g., `myVariable`, `myFunction`).
- Use PascalCase for class names (e.g., `MyClass`).
- Use UPPERCASE_WITH_UNDERSCORES for constants (e.g., `MAX_SIZE`).

``` js
// Examples
let firstName = 'John';
function calculateSum(a, b) {
  return a + b;
}
class UserModel {
  // class implementation
}
const MAX_RETRY_ATTEMPTS = 3;
```

## File Naming

When naming files in Node.js:

- Use camelCase for file names.
- Choose descriptive names that reflect the file's purpose.
- Be consistent across your project.

Example:

```plaintext
project-root/
|-- src/
|   |-- controllers/
|       |-- userController.js
|       |-- authController.js
|   |-- models/
|       |-- userModel.js
|   |-- utils/
|       |-- dataHandler.js
|-- index.js
|-- package.json
```

## Import Conventions

### Library Imports

When importing external libraries, use clear and concise names.

Example:

```javascript
const express = require('express');
const fs = require('fs');
```

### Absolute Imports

Organize absolute imports in alphabetical order.

Example:

```javascript
const config = require('config');
const utils = require('./utils');
const userModel = require('../models/userModel');
```

### Relative Imports

Similar to absolute imports, organize relative imports alphabetically.

Example:

```javascript
const helper = require('./helper');
const constants = require('../constants');
```

## Alignment

Maintain consistent code alignment for improved readability.

Example:

```javascript
const variable1   = 'value1';
const variable2   = 'value2';
const longVariable = 'longValue';
```

## Quotes

Consistent use of single or double quotes throughout the project.

Example:

```javascript
const singleQuotes = 'This is a string';
const doubleQuotes = "This is another string";
```

## Spacing

Follow consistent spacing conventions for better code readability.

Example:

```javascript
function addNumbers(a, b) {
  return a + b;
}
```

## Testing

Implement unit testing to ensure the correctness of individual units of code.

Example:

```javascript
// test/example.test.js
const { addNumbers } = require('../src/utils');

test('adds two numbers correctly', () => {
  expect(addNumbers(2, 3)).toBe(5);
});
```

## Linting

Use a linter to enforce consistent coding style and catch common errors.

Example:

```plaintext
# .eslintrc.js
module.exports = {
  extends: 'eslint:recommended',
  rules: {
    // your rules here
  },
};
```

## Logging

Logging is crucial for debugging, monitoring, and gaining insights into the behavior of your Node.js application. Follow these guidelines for effective logging:

### 1. Use a Logging Library

   Choose a logging library that suits your needs, such as [Winston](https://github.com/winstonjs/winston) or [Bunyan](https://github.com/trentm/node-bunyan). These libraries provide flexible and customizable logging options.

### 2. Log Levels

   Utilize different log levels (e.g., info, warn, error) based on the severity of the message. This helps in categorizing and filtering logs.

   ```javascript
   const logger = require('winston');

   logger.info('Informational message');
   logger.warn('Warning message');
   logger.error('Error message');
   ```

### 3. Include Contextual Information

   Enhance logs with contextual information like timestamps, request/response details, or user-specific data. This aids in better understanding the log events.

   ```javascript
   const logger = require('winston');

   logger.info('User login', { username: 'john_doe', timestamp: new Date() });
   ```

### 4. Log to Files or External Services

   Consider logging to files for local development and debugging. In production, configure the logger to send logs to external services like [Loggly](https://www.loggly.com/) or [ELK Stack](https://www.elastic.co/what-is/elk-stack).

### 5. Monitor Logs

   Regularly review and monitor logs. Set up alerts for critical errors to respond promptly to issues.

### Example Using Winston

```javascript
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  defaultMeta: { service: 'your-service-name' },
  transports: [
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' }),
  ],
});

if (process.env.NODE_ENV !== 'production') {
  logger.add(new winston.transports.Console());
}

logger.info('Application started');

// Example of logging an error
try {
  throw new Error('This is a test error');
} catch (error) {
  logger.error('An error occurred:', error);
}
```

## Anti-Patterns

When working with Node.js, it's essential to be aware of and avoid common anti-patterns that can lead to issues in your code. Consider the following anti-patterns and strive to follow best practices instead:

### 1. Callback Hell (Pyramid of Doom)

   Writing deeply nested callbacks can lead to unreadable and hard-to-maintain code. Instead, consider using Promises, async/await, or other control flow libraries to handle asynchronous operations more cleanly.

   ```javascript
   fs.readFile('file1.txt', (err, data1) => {
     fs.readFile('file2.txt', (err, data2) => {
       // Nested operations
     });
   });
   ```

### 2. Blocking the Event Loop

   Avoid blocking the event loop with long-running synchronous operations, as it can lead to poor application performance and responsiveness.

   ```javascript
   const result = fs.readFileSync('file.txt');
   // Blocking operation
   ```

### 3. Global Variables

   Excessive use of global variables can lead to naming conflicts and unintended side effects. Limit the use of global variables and prefer encapsulation.

   ```javascript
   global.counter = 0;
   // Global variable usage
   ```

### 4. Overusing `console.log` for Debugging

   While `console.log` is handy for debugging, overusing it in production code can clutter the console and impact performance. Consider using proper logging libraries.

   ```javascript
   console.log('Debugging information');
   ```

### 5. Ignoring Error Handling

   Neglecting proper error handling can lead to unexpected behavior and make debugging challenging. Always handle errors appropriately, whether through logging, throwing, or returning.

   ```javascript
   fs.readFile('file.txt', (err, data) => {
     // Error handling missing
   });
   ```

### 6. Excessive Dependencies

   Adding unnecessary dependencies can bloat your project and introduce potential security vulnerabilities. Only include dependencies that are essential for your project.

   ```json
   // Excessive dependencies
   "dependencies": {
     "library1": "^1.0.0",
     "library2": "^2.0.0",
     "library3": "^3.0.0"
   }
   ```

### 7. Inefficient String Concatenation

   Repeatedly concatenating strings using the `+` operator can be inefficient. Instead, use template literals or array join for better performance.

   ```javascript
   const result = 'Hello' + ' ' + 'World';
   ```

### 8. Not Scaling Your Application

   Failing to design your application with scalability in mind can lead to performance bottlenecks as your project grows. Consider modularizing and optimizing for scalability from the beginning.

   ```javascript
   // Lack of scalability considerations
   ```

### 9. Ignoring Security Best Practices

   Neglecting security best practices, such as input validation and secure coding practices, can expose your application to vulnerabilities. Always prioritize security in your development process.

   ```javascript
   // Lack of input validation
   ```

These anti-patterns can hinder the maintainability, performance, and security of your Node.js applications. Be mindful of these pitfalls and strive to adopt best practices for a more robust and efficient codebase.

## Best Practices

Consider the following best practices:

- Use version control (e.g., Git) for tracking changes.
- Implement meaningful commit messages.
- Utilize a package manager (e.g., npm or yarn) for managing dependencies.
- Regularly update dependencies to benefit from the latest features and security fixes.

## Contributing

We welcome contributions! If you have any questions or suggestions, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
