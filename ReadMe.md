# React Naming Standards

## Table of Contents

- [React Naming Standards](#react-naming-standards)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Folder Structure](#folder-structure)
  - [Basic Rules](#basic-rules)
  - [Naming Conventions](#naming-conventions)
  - [Library Imports](#library-imports)
  - [Absolute Imports](#absolute-imports)
  - [Relative Imports](#relative-imports)
  - [Alignment](#alignment)
  - [Quotes](#quotes)
  - [Spacing](#spacing)
  - [Props](#props)
  - [Refs](#refs)
  - [Parentheses](#parentheses)
  - [Tags](#tags)
  - [Examples](#examples)
    - [MyComponent.js](#mycomponentjs)
  - [ReactJS Development Rules](#reactjs-development-rules)
  - [Mixins](#mixins)
  - [Contributing](#contributing)
  - [License](#license)

## Introduction

Welcome to the documentation for React Naming Standards and Best Practices! This document provides guidelines and best practices to help you understand the project structure, naming conventions, and coding standards.

## Folder Structure

Our project should follow a well-organized folder structure to maintain clarity, consistency and simplicity. Here's an overview:

```plaintext
project-root/
  ├── src/
  │   ├── components/
  │   │   ├── Component1/
  │   │   │   ├── Component1.js
  │   │   │   └── Component1.test.js
  │   │   └── Component2/
  │   │       ├── Component2.js
  │   │       └── Component2.test.js
  │   ├── styles/
  │   │   ├── global.css
  │   │   ├── common.css
  │   │   ├── Component1Styles.css
  │   │   ├── Component2Styles.css
  │   ├── utils/
  │   │   ├── utilityFunction.js
  │   │   └── HelperFunction.js
  │   ├── services/
  │   │   └── ApiService.js
  │   ├── assets/
  │   │   ├── images/
  │   │   │   └── image1.png
  │   │   │   └── image2.png
  │   │   ├── fonts/
  │   │   │   └── font1.ttf
  │   │   └── other/
  │   │       └── otherAsset.ext
  │   ├── App.js
  │   ├── index.js
  │   ├── index.css
  │   └── setupTests.js
  ├── public/
  │   ├── index.html
  │   ├── favicon.ico
  │   └── ...
  ├── data/
  │   └── data.json
  ├── README.md
  ├── package.json
  └── ...

```

## Basic Rules

- Only include one React component per file. However, multiple Stateless or Pure Components are allowed per file. `eslint: react/no-multi-comp`.
- Always use JSX syntax.
- Do not use `React.createElement` unless you’re initializing the app from a file that is not JSX.

## Naming Conventions

- **PascalCase**: Use PascalCase for component names and Component file names. For example: `MyComponent`.
- **CamelCase**: Use camelCase for utility or helper files and folder names. For example: `commonUtils.js` or `commonFolder`
- **Extensions**: Use `.jsx` extension for React components. 
- **Reference Naming**: Use camelCase for componenet instances. 
  - *bad*
    ```jsx
    import reservationCard from './ReservationCard';
    const ReservationItem = <ReservationCard />;
    ```
  - *good*
    ```jsx
    import ReservationCard from './ReservationCard';
    const reservationItem = <ReservationCard />;
    ```
- **Component Naming**: Use the filename as the component name. For example, `ReservationCard.jsx` should have a reference name of `ReservationCard`. However, for root components of a directory, use `index.jsx` as the filename and use the directory name as the component name:
  - *bad*
    ```jsx
    import Footer from './Footer/Footer';
    import Footer from './Footer/index';
    ```
  - *good*
    ```jsx
    import Footer from './Footer';
    ```
- **Alphabetical Order**: Maintain alphabetical order for imports and file organization.
- The following import priority should be followed: 

```plaintext  
  ├──Library imports
  ├──Absolute imports from the project
  ├──Relative imports
``````

## Library Imports

```jsx
// React Imports
import React from 'react';
import ReactDOM from 'react-dom';

// External Libraries
import axios from 'axios';
import { BrowserRouter as Router, Route } from 'react-router-dom';
import moment from 'moment';
```

## Absolute Imports

```jsx
// Custom or Absolute Imports
import MyComponent from 'components/MyComponent';
import utilityFunction from 'utils/utilityFunction';
import ApiService from 'services/ApiService';
import HelperFunction from 'utils/HelperFunction';
```

## Relative Imports

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

## Alignment

- Follow these alignment styles for JSX syntax. 
  
  - *bad*
    ```jsx
    <Foo superLongParam="bar"
         anotherSuperLongParam="baz" />
    ```
  - *good*
    ```jsx
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    />
    ```
    *or, if props fit in one line*
    ```jsx
    <Foo bar="bar" />
    ```
    *children get indented normally*
    ```jsx
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    >
      <Quux />
    </Foo>
    ```
    *good*
    ```jsx
    {showButton && (
      <Button />
    )}
    {showButton && <Button />}
    ```
    *good*
    ```jsx
    {someReallyLongConditional
      && anotherLongConditional
      && (
        <Foo
          superLongParam="bar"
          anotherSuperLongParam="baz"
        />
      )
    }
    ```
    *good*
    ```jsx
    {someConditional ? (
      <Foo />
    ) : (
      <Foo
        superLongParam="bar"
        anotherSuperLongParam="baz"
      />
    )}
  
## Quotes

- Always use double quotes (`"`) for JSX attributes, but single quotes (`'`) for all other JS. `eslint: jsx-quotes`
  - *bad*
    ```jsx
    <Foo bar='bar' />
    <Foo style={{ left: "20px" }} />
    ```
  - *good*
    ```jsx
    <Foo bar="bar" />
    <Foo style={{ left: '20px' }} />
    ```

## Spacing

- Always include a single space in your self-closing tag. `eslint: no-multi-spaces, react/jsx-tag-spacing`
  - *bad*
    ```jsx
    <Foo/>
    <Foo                 />
    <Foo
     />
    ```
  - *good*
    ```jsx
    <Foo />
    ```

- Do not pad JSX curly braces with spaces. `eslint: react/jsx-curly-spacing`
  - *bad*
    ```jsx
    <Foo bar={ baz } />
    ```
  - *good*
    ```jsx
    <Foo bar={baz} />
    ```

## Props

- Always use camelCase for prop names, or PascalCase if the prop value is a React component.
  - *bad*
    ```jsx
    <Foo UserName="hello" phone_number={12345678} />
    ```
  - *good*
    ```jsx
    <Foo userName="hello" phoneNumber={12345678} Component={SomeComponent} />
    ```

- Omit the value of the prop when it is explicitly true.
  - *bad*
    ```jsx
    <Foo hidden={true} />
    ```
  - *good*
    ```jsx
    <Foo hidden />
    ```

  - *good*
    ```jsx
    <Foo hidden />
    ```

- Always include an `alt` prop on `<img>` tags. If the image is presentational, `alt` can be an empty string or the `<img>` must have `role="presentation"`. 
  
  - *bad*
    ```jsx
    <img src="hello.jpg" />
    ```
  - *good*
    ```jsx
    <img src="hello.jpg" alt="Me waving hello" />
    ```
  - *good*
    ```jsx
    <img src="hello.jpg" alt="" />
    ```
  - *good*
    ```jsx
    <img src="hello.jpg" role="presentation" />
    ```

- Do not use words like "image", "photo", or "picture" in `<img>` `alt` props. 
  
  - *bad*
    ```jsx
    <img src="hello.jpg" alt="Picture of me waving hello" />
    ```
  - *good*
    ```jsx
    <img src="hello.jpg" alt="Me waving hello" />
    ```

- Use only valid, non-abstract ARIA roles.

  - *bad - not an ARIA role*
    ```jsx
    <div role="datepicker" />
    ```
  - *bad - abstract ARIA role*
    ```jsx
    <div role="range" />
    ```
  - *good*
    ```jsx
    <div role="button" />
    ```

- Do not use `accessKey` on elements.
  - *bad*
    ```jsx
    <div accessKey="h" />
    ```

  - *good*
    ```jsx
    <div />
    ```

## Refs

- Always use ref callbacks.
  - *bad*
    ```jsx
    <Foo ref="myRef" />
    ```
  - *good*
    ```jsx
    <Foo ref={(ref) => { this.myRef = ref; }} />
    ```

## Parentheses

- Wrap JSX tags in parentheses when they span more than one line.
  
  - *bad*
    ```jsx
    render() {
      return <MyComponent variant="long body" foo="bar">
               <MyChild />
             </MyComponent>;
    }
    ```
  - *good*
    ```jsx
    render() {
      return (
        <MyComponent variant="long body" foo="bar">
          <MyChild />
        </MyComponent>
      );
    }
    ```

## Tags

- Always self-close tags that have no children.
  
  - *bad*
    ```jsx
    <Foo variant="stuff"></Foo>
    ```
  - *good*
    ```jsx
    <Foo variant="stuff" />
    ```

- If your component has multiline properties, close its tag on a new line.
  
  - *bad*
    ```jsx
    <Foo
      bar="bar"
      baz="baz" />
    ```
  - *good*
    ```jsx
    <Foo
      bar="bar"
      baz="baz"
    />
    ```

## Examples

Here are some examples of how to structure and organize your code following the outlined guidelines.

### MyComponent.js

```jsx
import React from 'react';
import './MyComponentStyles.css';
import { formatDate } from './utils/dateUtils';
import { calculateTotal } from './utils/mathUtils';

const MyComponent = () => {
  // Component logic here

  return (
    <div>
      {/* JSX content */}
    </div>
  );
};

export default MyComponent;
```

## ReactJS Development Rules

1. **Exception Handling:**
   - Implement proper exception handling in your code to gracefully manage errors.
   - Utilize try-catch blocks where necessary to capture and handle exceptions.
   - **Example:**
     ```javascript
     try {
       // code that may throw an exception
     } catch (error) {
       // handle the exception
     }
     ```

2. **Logging:**
   - Include logging statements strategically in your code to aid in debugging and monitoring.
   - Use appropriate log levels based on the nature and severity of the logged information.
   - **Libraries:**
     - [Winston](https://github.com/winstonjs/winston)
     - [Bunyan](https://github.com/trentm/node-bunyan)
   - **Example:**
     ```javascript
     const winston = require('winston');

     winston.info('This is an informational message.');
     winston.error('An error occurred:', error);
     ```

3. **Unit Testing:**
   - Include unit test cases for your ReactJS components and Node.js modules.
   - Follow Test-Driven Development (TDD) principles to write tests before implementing the actual functionality.
   - **Libraries:**
     - [Jest](https://jestjs.io/)
     - [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
   - **Example:**
     ```javascript
     test('should render MyComponent correctly', () => {
       const { getByText } = render(<MyComponent />);
       expect(getByText('Hello World')).toBeInTheDocument();
     });
     ```

4. **Linting:**
   - Apply linting tools to maintain code consistency and catch potential errors early.
   - Use a linter (e.g., ESLint) with a predefined set of rules to ensure code quality.
   - **Libraries:**
     - [ESLint](https://eslint.org/)
   - **Example:**
     - Create an `.eslintrc.js` file with configuration settings.

5. **ReactJS Fixes:**
   - Fix small functionality for each ReactJS file to ensure a high level of code quality.
   - Pay attention to details and address any issues that might impact the performance or maintainability of the code.

6. **Avoid Inline CSS:**
   - Minimize the use of inline CSS in your React components.
   - Prefer external stylesheets or styled-components for a cleaner and more maintainable styling approach.

7. **Split Code into Smaller Functions:**
   - Break down your code into multiple smaller functions to enhance readability and maintainability.
   - Each function should have a clear and specific purpose, promoting modular and reusable code.
   - **Example:**
     ```javascript
     function calculateTotalPrice(items) {
       // logic to calculate total price
     }

     function displayReceipt(totalPrice) {
       // logic to display receipt
     }
     ```

8. **Create Utility Files:**
   - Develop utility files to house common functions and avoid duplicate code across multiple files.
   - Encapsulate reusable logic in separate utility functions to promote code organization and reduce redundancy.
   - **Example:**
     - Creating `dateUtils.js` for date-related functions.

9. **Logical File Naming:**
   - Name your files logically based on the specific tasks or functionality they perform.
   - Follow a consistent and descriptive naming convention to make it easier for developers to understand the purpose of each file.
   - **Example:**
     - Naming a file `apiService.js` for handling API-related tasks.

10. **TDD Development for Unit Test Cases:**
    - Adopt a Test-Driven Development (TDD) approach when creating unit test cases.
    - Write test cases before implementing new features or fixing issues to ensure comprehensive test coverage.
    - **Example:**
      - Writing a test case for a component before implementing its functionality.




## Mixins

- Do not use mixins.
  - Why? Mixins introduce implicit dependencies, cause name clashes, and cause snowballing complexity. Most use cases for mixins can be accomplished in better ways via components, higher-order components, or utility modules.


## Contributing

We welcome contributions! If you have any questions or suggestions, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).