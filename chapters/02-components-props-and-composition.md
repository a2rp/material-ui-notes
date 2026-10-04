# 2. Components, props, and composition

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Getting started with Material UI](./01-getting-started-with-material-ui.md) | [Notes index](../README.md) | [Next: Typography, surfaces, and layout](./03-typography-surfaces-and-layout.md) |

## Components are React elements

A Material UI component is used like a React component. You import it, pass props, and provide child elements when needed:

~~~jsx
import Alert from '@mui/material/Alert';

export default function SaveMessage() {
  return <Alert severity="success">Changes saved</Alert>;
}
~~~

The component owns its internal markup and interaction. Props are the supported way to choose behavior, appearance, content, and state.

## Read the component API

Before choosing a prop, open that component's API page. Check its accepted values, default behavior, accessibility notes, and which element it renders. Names that look similar can still belong to different component APIs.

Common prop groups include:

| Prop group | Examples | Purpose |
| --- | --- | --- |
| Content | <code>children</code>, <code>label</code> | Supply visible content |
| Appearance | <code>variant</code>, <code>color</code>, <code>size</code> | Select a documented style |
| State | <code>disabled</code>, <code>selected</code>, <code>loading</code> | Describe component state |
| Layout | <code>sx</code>, <code>fullWidth</code> | Control sizing and styles |
| Events | <code>onClick</code>, <code>onChange</code> | Respond to user input |

Not every component accepts every prop. Type an event callback on the element that emits the event and use the event or value supplied by that callback.

## Children and composition

A parent component can contain other components. This is composition: build a larger interface by combining small parts.

~~~jsx
import Button from '@mui/material/Button';
import Card from '@mui/material/Card';
import CardActions from '@mui/material/CardActions';
import CardContent from '@mui/material/CardContent';
import Typography from '@mui/material/Typography';

export default function ProjectCard() {
  return (
    <Card>
      <CardContent>
        <Typography variant="h6" component="h2">
          Linux notes
        </Typography>
        <Typography color="text.secondary">
          A practical reference for everyday commands.
        </Typography>
      </CardContent>
      <CardActions>
        <Button href="/notes">Open notes</Button>
      </CardActions>
    </Card>
  );
}
~~~

The component tree stays readable when each component has a clear job. Extract a React component when a section is reused or has enough behavior to understand separately.

## Preserve semantic HTML

Visual appearance and HTML meaning are separate choices. The <code>component</code> prop can render an appropriate element while keeping the component styles:

~~~jsx
import Button from '@mui/material/Button';
import Typography from '@mui/material/Typography';

export default function PageHeading() {
  return (
    <>
      <Typography variant="h4" component="h1">
        Projects
      </Typography>
      <Button href="/projects">Browse projects</Button>
    </>
  );
}
~~~

Use a heading element for a heading and an anchor for navigation. A button performs an action, while a link moves to another location. Material UI components that receive an <code>href</code> generally render as links.

## Pass props through a small wrapper

A reusable wrapper should expose the props callers need and forward them to the underlying Material UI component:

~~~jsx
import Button from '@mui/material/Button';

export function PrimaryAction({ children, ...buttonProps }) {
  return (
    <Button variant="contained" {...buttonProps}>
      {children}
    </Button>
  );
}
~~~

Here the wrapper sets a consistent default variant, while a caller can still provide an event handler, accessible label, or other documented Button prop. Avoid accepting arbitrary props and spreading them onto a native DOM element without checking what they do.

## Keep the component API clear

Prefer documented props over selectors that depend on generated class names or internal markup. If a prop is missing, compose a small React component or use a supported slot API instead of reaching into private implementation details.

## Practice questions

1. What is the supported way to configure a Material UI component?
2. Why should you check the component API page before using a prop?
3. What does the <code>children</code> prop represent?
4. What does component composition mean?
5. When is an anchor a better semantic choice than a button?
6. What does the <code>component</code> prop let you change?
7. Why should a reusable wrapper forward useful component props?
8. Why should application code avoid depending on generated internal class names?

## References

- [Material UI usage](https://mui.com/material-ui/getting-started/usage/)
- [Material UI component API pages](https://mui.com/material-ui/all-components/)
- [Composition guide](https://mui.com/material-ui/guides/composition/)
- [React component composition](https://react.dev/learn/passing-props-to-a-component)