# 13. Accessibility and keyboard navigation

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Responsive layouts and breakpoints](./12-responsive-layouts-and-breakpoints.md) | [Notes index](../README.md) | [Next: React state and controlled components](./14-react-state-and-controlled-components.md) |

## Keep the interface semantic

Use HTML elements and Material UI components according to their purpose. Use headings for sections, links for navigation, buttons for actions, and lists or tables for grouped data. A visual style does not provide the meaning of an element by itself.

Keep headings in a logical order. Place navigation links in a labeled <code>nav</code> region. A page can contain multiple navigation regions if each one has a distinct accessible label.

## Label every control

A person using a screen reader should be able to identify each input and what value it expects. TextField provides a visible label:

~~~jsx
import TextField from '@mui/material/TextField';

export default function SearchField() {
  return (
    <TextField
      fullWidth
      label="Search notes"
      name="search"
      type="search"
    />
  );
}
~~~

For grouped controls, associate labels with the controls:

~~~jsx
import Checkbox from '@mui/material/Checkbox';
import FormControlLabel from '@mui/material/FormControlLabel';

export default function UpdatesPreference() {
  return (
    <FormControlLabel
      control={<Checkbox name="updates" />}
      label="Email me account updates"
    />
  );
}
~~~

An icon-only button needs an accessible name because it has no visible text:

~~~jsx
import IconButton from '@mui/material/IconButton';
import MenuIcon from '@mui/icons-material/Menu';

export default function MenuButton() {
  return (
    <IconButton aria-label="Open navigation">
      <MenuIcon aria-hidden="true" />
    </IconButton>
  );
}
~~~

A tooltip can explain an icon to sighted users, but the button still needs its own accessible name.

## Preserve keyboard behavior

Use built-in Button, Link, Menu, Dialog, and Tabs interactions instead of recreating them with generic elements and click handlers. Check that every action can be reached and used with a keyboard.

Tab moves focus through interactive controls. Enter or Space activates many buttons. Escape commonly closes menus and dialogs. The exact key behavior depends on the component, so check the component documentation and test the interface.

## Make focus visible

Keyboard users need to see which control currently has focus. Do not remove focus outlines without providing a clear replacement. Test the focus appearance against every background and state.

When a Dialog or temporary Drawer opens, focus moves into that surface. When it closes, focus should return to the control that opened it, unless that control no longer exists.

## Use more than color

Do not communicate an error, selection, or success using color alone. Pair color with a visible label, icon with an accessible name, or another clear cue. Check text and control contrast in normal, hover, disabled, and focus states.

Keep user text at the browser zoom level readable. Responsive layouts should still work when the page is enlarged and when text wraps onto multiple lines.

## Practice questions

1. Which element should be used for navigation to another page?
2. Why should a heading look and behave like a heading in the HTML structure?
3. What identifies the purpose of a TextField?
4. What must an icon-only button include?
5. Does a tooltip replace an accessible button name?
6. Why should focus remain visible?
7. What should happen to focus when a Dialog closes?
8. Why is color alone insufficient to communicate an error?

## References

- [Material UI accessibility](https://mui.com/material-ui/guides/accessibility/)
- [Button accessibility](https://mui.com/material-ui/react-button/#accessibility)
- [Dialog accessibility](https://mui.com/material-ui/react-dialog/#accessibility)
- [Tabs accessibility](https://mui.com/material-ui/react-tabs/#accessibility)
- [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG22/)