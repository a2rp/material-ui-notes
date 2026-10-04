# 1. Getting started with Material UI

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Notes index](../README.md) | [Notes index](../README.md) | [Next: Components, props, and composition](./02-components-props-and-composition.md) |

## What Material UI provides

Material UI is a React component library. It provides ready-made interface pieces such as buttons, text fields, dialogs, navigation, and layout components. The components handle common interaction and accessibility behavior, while props and themes let an application adapt their appearance.

Material UI is one library in the MUI family. This repository focuses on the Material UI package named <code>@mui/material</code>. MUI X components such as Data Grid are separate packages.

## Install the packages

Begin with an existing React application. React and React DOM must already be installed because they are peer dependencies. The default styling engine uses Emotion:

~~~sh
npm install @mui/material @emotion/react @emotion/styled
~~~

Roboto is the default typeface. Install Fontsource if the app should bundle the font locally:

~~~sh
npm install @fontsource/roboto
~~~

The Material Icons React components are optional and installed separately:

~~~sh
npm install @mui/icons-material
~~~

Use package versions that fit the React app. When working in an existing project, keep its lockfile and use the package manager already used by that project.

## Add a first component

Import the component and render it like a normal React element. Props select its appearance and behavior:

~~~jsx
import Button from '@mui/material/Button';

export default function Welcome() {
  return (
    <main>
      <h1>My first Material UI component</h1>
      <Button
        variant="contained"
        onClick={() => window.alert('The button works')}
      >
        Try the button
      </Button>
    </main>
  );
}
~~~

The component is still part of the React tree. Data, event handlers, and conditional rendering work with the same React patterns used by other components.

## Set up the application entry

Import the font weights used by the app and place <code>CssBaseline</code> near the root. It applies a consistent set of base styles:

~~~jsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import CssBaseline from '@mui/material/CssBaseline';
import '@fontsource/roboto/400.css';
import '@fontsource/roboto/500.css';
import App from './App.jsx';

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <CssBaseline />
    <App />
  </StrictMode>
);
~~~

The HTML page should include a responsive viewport meta tag so the layout uses the device width on mobile screens:

~~~html
<meta name="viewport" content="initial-scale=1, width=device-width" />
~~~

Some projects load Roboto from a font CDN instead. Local font files reduce dependence on that remote request and let the bundler include only the weights the app uses.

## Import only what the screen uses

Import components from their package paths or from the package entry point:

~~~jsx
import Button from '@mui/material/Button';
import { Stack, Typography } from '@mui/material';
~~~

Both styles are supported. Clear imports make dependencies easy to find. Keep component imports focused on what the screen actually renders.

## Practice questions

1. What does Material UI provide to a React application?
2. Which package contains the standard Material UI components?
3. Why must React and React DOM already be installed?
4. Which styling engine is used by the default installation?
5. Are MUI X components included in the Material UI package?
6. What does the Button <code>variant</code> prop change in the example?
7. What does <code>CssBaseline</code> provide?
8. Why does a page need a responsive viewport meta tag?

## References

- [Material UI overview](https://mui.com/material-ui/getting-started/)
- [Material UI installation](https://mui.com/material-ui/getting-started/installation/)
- [Material UI usage](https://mui.com/material-ui/getting-started/usage/)