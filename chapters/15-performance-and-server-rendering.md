# 15. Performance and server rendering

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: React state and controlled components](./14-react-state-and-controlled-components.md) | [Notes index](../README.md) | [Next: Testing and production patterns](./16-testing-and-production-patterns.md) |

## Measure before optimizing

Start by checking which part of the page is slow. A slow initial load, a delayed response to input, and a large bundle have different causes. Use the browser performance tools and the framework production build before changing component code.

Avoid adding memoization everywhere. First find work that is repeated and expensive, then compare the result after a targeted change. Reuse a theme object rather than recreating it on every render.

## Keep imports focused

Import components from their package paths:

~~~jsx
import Button from '@mui/material/Button';
import TextField from '@mui/material/TextField';
import AddIcon from '@mui/icons-material/Add';
~~~

Modern production bundlers can tree-shake unused exports from top-level imports, but broad package imports can slow development startup and rebuilds. Direct icon paths are particularly helpful when importing from the large icon package.

Use only the packages and components that the application needs. MUI X packages are separate from Material UI and should be installed only when their features are needed.

## Keep large views responsive

For a large dataset, choose a component designed for the required data interaction. MUI X Data Grid virtualizes rows so a large list does not need to render every row at once. Keep row data and column definitions stable when possible, and do not put expensive calculations directly in every cell render.

Measure bundle size and interaction performance on representative data. A small example dataset can hide costs that appear on a production-sized screen.

## Server-render the initial styles

Material UI uses Emotion by default. With server rendering, the server and browser need compatible theme and style configuration so the first page includes the component CSS. Incorrect setup can cause the page to appear without its intended styles until the client adds them.

Use the official integration for the framework and router in the application. Framework adapters manage the style collection and insertion behavior. When writing a custom server rendering integration, create a fresh Emotion cache for each request and use the same cache configuration during hydration.

Do not copy a server setup from a different framework version without checking the current integration guide. Package names and router adapters can change.

## Keep client and server output aligned

The theme should be configured consistently on the server and client. Avoid choosing markup based on browser-only values during the initial render unless the framework supports that pattern. Responsive client behavior may begin with an unknown viewport on the server, so verify that hydration does not replace the first layout unexpectedly.

## Practice questions

1. Why should performance changes start with measurement?
2. Why can broad package imports slow development even when production tree-shakes unused code?
3. Which import form is recommended for Material UI icons?
4. Why is Data Grid useful for a large dataset?
5. Which styling engine is used by the default Material UI setup?
6. What can happen when server-rendered styles are not collected correctly?
7. Why should a custom server render use a new Emotion cache for each request?
8. Why must server and browser theme configuration match?

## References

- [Minimizing bundle size](https://mui.com/material-ui/guides/minimizing-bundle-size/)
- [Server rendering](https://mui.com/material-ui/guides/server-rendering/)
- [Next.js integration](https://mui.com/material-ui/integrations/nextjs/)
- [MUI X Data Grid performance](https://mui.com/x/react-data-grid/performance/)