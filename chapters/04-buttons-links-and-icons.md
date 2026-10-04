# 4. Buttons, links, and icons

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Typography, surfaces, and layout](./03-typography-surfaces-and-layout.md) | [Notes index](../README.md) | [Next: Forms and input controls](./05-forms-and-input-controls.md) |

## Choose a button style

Material UI Button supports three common variants:

~~~jsx
import Button from '@mui/material/Button';
import Stack from '@mui/material/Stack';

export default function ButtonExamples() {
  return (
    <Stack direction="row" spacing={2}>
      <Button variant="text">Text</Button>
      <Button variant="outlined">Outlined</Button>
      <Button variant="contained">Contained</Button>
    </Stack>
  );
}
~~~

Use a contained button for the primary action on a view. Use outlined and text buttons for supporting actions. Keep the number of competing primary actions small.

The <code>color</code> prop selects a theme color and <code>size</code> controls the component size. Prefer the theme palette over custom colors for consistent contrast:

~~~jsx
import Button from '@mui/material/Button';

export default function SaveButton() {
  return (
    <Button color="success" size="large" variant="contained">
      Save changes
    </Button>
  );
}
~~~

## Use a link for navigation

A link navigates. A button performs an action. Material UI Button renders as an anchor when it receives an <code>href</code>:

~~~jsx
<Button href="/settings" variant="outlined">
  Open settings
</Button>
~~~

Use the Link component for text links:

~~~jsx
import Link from '@mui/material/Link';

export default function HelpLink() {
  return (
    <Link href="/help" underline="hover">
      Read help
    </Link>
  );
}
~~~

For a client-side routing library, connect its link component through the Material UI component integration pattern. This preserves normal anchor behavior such as opening a destination in a new tab.

## Add icons with meaning

Install <code>@mui/icons-material</code> separately. Use an icon alongside a clear label when the action needs to be easy to recognize:

~~~jsx
import AddIcon from '@mui/icons-material/Add';
import Button from '@mui/material/Button';

export default function AddButton() {
  return (
    <Button startIcon={<AddIcon />} variant="contained">
      Add project
    </Button>
  );
}
~~~

For an icon-only control, provide an accessible name. A tooltip helps sighted users discover the action, but the accessible label still belongs on the control:

~~~jsx
import DeleteIcon from '@mui/icons-material/Delete';
import IconButton from '@mui/material/IconButton';
import Tooltip from '@mui/material/Tooltip';

export default function DeleteButton() {
  return (
    <Tooltip title="Delete project">
      <IconButton aria-label="Delete project" color="error">
        <DeleteIcon />
      </IconButton>
    </Tooltip>
  );
}
~~~

Do not add a second accessible label to a decorative icon beside visible text. In a button with text, the label already explains the action.

## Group related choices

Use <code>ButtonGroup</code> when a small set of related actions should appear together:

~~~jsx
import Button from '@mui/material/Button';
import ButtonGroup from '@mui/material/ButtonGroup';

export default function ViewChoices() {
  return (
    <ButtonGroup aria-label="Choose a view">
      <Button>List</Button>
      <Button>Grid</Button>
    </ButtonGroup>
  );
}
~~~

A group is for related choices, not a way to combine unrelated actions into one control.

## Practice questions

1. What are the three common Button variants?
2. Which variant is usually suitable for the primary action?
3. When does Button render as an anchor?
4. What should a navigation action use, a link or a button?
5. Why does an icon-only control need an accessible name?
6. Is a tooltip a replacement for the icon button label?
7. Which prop places an icon before Button content?
8. When is ButtonGroup useful?

## References

- [Button](https://mui.com/material-ui/react-button/)
- [Link](https://mui.com/material-ui/react-link/)
- [IconButton](https://mui.com/material-ui/react-button/#icon-button)
- [Material Icons](https://mui.com/material-ui/material-icons/)
- [Tooltip](https://mui.com/material-ui/react-tooltip/)