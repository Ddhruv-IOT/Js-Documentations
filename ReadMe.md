# React Naming Standards

## Table of Contents

- [React Naming Standards](#react-naming-standards)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Folder Structure](#folder-structure)
  - [Naming Conventions](#naming-conventions)
  - [Library Imports](#library-imports)
  - [Absolute Imports](#absolute-imports)
  - [Relative Imports](#relative-imports)
  - [Examples](#examples)
    - [MyComponent.js](#mycomponentjs)
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

## Naming Conventions

- **PascalCase**: Use PascalCase for component names. For example: `MyComponent`.
- **CamelCase**: Use camelCase for utility or helper files and folder names. For example: `commonUtils.js` or `commonFolder`
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

## Contributing

We welcome contributions! If you have any questions or suggestions, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).