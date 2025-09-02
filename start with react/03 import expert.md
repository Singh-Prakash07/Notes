### Named vs. Default Exports in React
+ In React, the way you export your components directly affects how you must import them into other files. Understanding this is key to avoiding common rendering issues.
#### 1. Named Exports
+ A named export is used when you want to export multiple, specific variables or components from a single file. Each exported item has its own unique name.
+ Example of a Named Export:
+ In Button.jsx, you can export multiple components:
```
// Button.jsx
import React from 'react';

// This is a named export
export const PrimaryButton = ({ label }) => (
  <button className="bg-blue-500 text-white font-bold py-2 px-4 rounded">
    {label}
  </button>
);

// This is another named export
export const SecondaryButton = ({ label }) => (
  <button className="bg-gray-500 text-white font-bold py-2 px-4 rounded">
    {label}
  </button>
);
```
#### How to Import a Named Export:

+ To use these components in another file (e.g., App.jsx), you must import them by their exact names, enclosed in curly braces {}.
```
// App.jsx
import React from 'react';
import { PrimaryButton, SecondaryButton } from './Button';

const App = () => (
  <div>
    <PrimaryButton label="Click Me" />
    <SecondaryButton label="Cancel" />
  </div>
);
```
export default App;

If you tried to import them as import { Button } from './Button';, it would fail because the names do not match.

2. Default Exports
A default export is used to define a single, main export for a file. This is the most common method for exporting a single React component per file.

Example of a Default Export:

In HomePage.jsx, the primary component is exported as the default.

// HomePage.jsx
import React from 'react';

const HomePage = () => (
  <div className="text-center p-8">
    <h1 className="text-4xl font-bold text-gray-800">Welcome!</h1>
    <p className="mt-4 text-lg text-gray-600">This is the main home page.</p>
  </div>
);

// This is the default export
export default HomePage;

How to Import a Default Export:

When you import a default export, you can give it any name you want. You do not use curly braces.

// App.jsx
import React from 'react';
import HomePage from './HomePage'; // The name 'HomePage' can be anything

const App = () => (
  <div>
    <HomePage />
  </div>
);

export default App;

Why Your Code Wasn't Working
When you were using export const Home = ... (a named export) and the page was blank, it's very likely that your import statement looked like this:

import Home from './Home';

This syntax is for a default export. Since your component was a named export, the import statement didn't find the component, and therefore nothing was rendered on the page.

Switching to export default Home; fixed the issue because it made your export match your import statement.

Best Practices
One Component Per File: A common best practice in React is to have one main component per file and use export default for that component. This makes your project structure clear and easy to navigate.

Utility Functions: Use named exports for smaller, non-component functions or variables within the same file. For example, export const fetchData = () => {};.
