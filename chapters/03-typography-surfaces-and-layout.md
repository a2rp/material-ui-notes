# 3. Typography, surfaces, and layout

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Components, props, and composition](./02-components-props-and-composition.md) | [Notes index](../README.md) | [Next: Buttons, links, and icons](./04-buttons-links-and-icons.md) |

## Typography variants and HTML meaning

Use <code>Typography</code> to apply the theme's text styles. Its <code>variant</code> prop selects an appearance, while <code>component</code> chooses the rendered HTML element. Keep the heading order meaningful:

~~~jsx
import Typography from '@mui/material/Typography';

export default function SectionTitle() {
  return (
    <header>
      <Typography variant="h1" component="h1">
        Project notes
      </Typography>
      <Typography variant="body1" component="p">
        Practical examples for building React interfaces.
      </Typography>
    </header>
  );
}
~~~

A large visual style does not automatically make a line a heading. Use one top-level page heading, then headings for sections and subsections in order.

## Container, Box, and Stack

Choose a layout component based on the job:

- <code>Container</code> keeps content within a centered maximum width.
- <code>Box</code> is a flexible element for grouping and one-off layout styles.
- <code>Stack</code> arranges children in a row or column with consistent spacing.

~~~jsx
import Button from '@mui/material/Button';
import Container from '@mui/material/Container';
import Stack from '@mui/material/Stack';
import Typography from '@mui/material/Typography';

export default function NotesHeader() {
  return (
    <Container maxWidth="md">
      <Stack spacing={2}>
        <Typography variant="h1" component="h1">
          Material UI notes
        </Typography>
        <Typography color="text.secondary">
          Learn components by building small interface sections.
        </Typography>
        <Button variant="contained">Browse chapters</Button>
      </Stack>
    </Container>
  );
}
~~~

The default theme spacing unit is 8 pixels. A Stack spacing value of 2 uses two theme spacing units. Theme customization can change the spacing scale.

## Surfaces for related content

Use <code>Paper</code> for a simple surface and <code>Card</code> when a content item has a defined structure with content and actions.

~~~jsx
import Card from '@mui/material/Card';
import CardContent from '@mui/material/CardContent';
import Typography from '@mui/material/Typography';

export default function NoteCard() {
  return (
    <Card component="article">
      <CardContent>
        <Typography variant="h2" component="h2">
          Layout basics
        </Typography>
        <Typography color="text.secondary">
          Use containers and stacks to establish a clear reading width.
        </Typography>
      </CardContent>
    </Card>
  );
}
~~~

Choose elevation and borders with restraint. A page becomes difficult to scan when every section is placed in a raised card.

## Dividers and grouping

A <code>Divider</code> can separate related sections without adding extra card layers:

~~~jsx
import Divider from '@mui/material/Divider';
import Stack from '@mui/material/Stack';
import Typography from '@mui/material/Typography';

export default function TopicList() {
  return (
    <Stack divider={<Divider flexItem />} spacing={2}>
      <Typography component="h2" variant="h6">Components</Typography>
      <Typography component="h2" variant="h6">Theming</Typography>
      <Typography component="h2" variant="h6">Accessibility</Typography>
    </Stack>
  );
}
~~~

Use headings and whitespace as the main structure. A divider is a visual cue, not a substitute for a heading or a label.

## Practice questions

1. What does the Typography <code>variant</code> prop select?
2. Which prop can choose the HTML heading element?
3. What does Container help control?
4. Which layout component is useful for one-dimensional spacing?
5. What is the default Material UI theme spacing unit?
6. When is Card a useful choice?
7. Why should heading levels follow a meaningful order?
8. Does a Divider provide a semantic section heading?

## References

- [Typography](https://mui.com/material-ui/react-typography/)
- [Container](https://mui.com/material-ui/react-container/)
- [Stack](https://mui.com/material-ui/react-stack/)
- [Box](https://mui.com/material-ui/react-box/)
- [Paper](https://mui.com/material-ui/react-paper/)
- [Card](https://mui.com/material-ui/react-card/)