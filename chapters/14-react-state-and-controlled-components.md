# 14. React state and controlled components

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Accessibility and keyboard navigation](./13-accessibility-and-keyboard-navigation.md) | [Notes index](../README.md) | [Next: Performance and server rendering](./15-performance-and-server-rendering.md) |

## Keep UI state in React

Material UI components render interface and report user interactions through callbacks. React state holds values that affect what the screen displays. When state changes, React renders the component again with the latest values.

A controlled TextField reads its value from state and updates that state in <code>onChange</code>:

~~~jsx
import { useState } from 'react';
import Button from '@mui/material/Button';
import Stack from '@mui/material/Stack';
import TextField from '@mui/material/TextField';

export default function ProjectNameForm() {
  const [name, setName] = useState('');

  function handleSubmit(event) {
    event.preventDefault();
    window.alert('Saving project: ' + name);
  }

  return (
    <form onSubmit={handleSubmit}>
      <Stack spacing={2}>
        <TextField
          label="Project name"
          value={name}
          onChange={(event) => setName(event.target.value)}
        />
        <Button type="submit" variant="contained" disabled={!name.trim()}>
          Save project
        </Button>
      </Stack>
    </form>
  );
}
~~~

The button is disabled until the state contains a non-whitespace value. This is derived from the state, so it does not need a second boolean state variable.

## Control a Select and Checkbox

Some inputs use a different value shape. A Select reports its chosen value, and a Checkbox reports whether it is checked:

~~~jsx
import { useState } from 'react';
import Checkbox from '@mui/material/Checkbox';
import FormControlLabel from '@mui/material/FormControlLabel';
import MenuItem from '@mui/material/MenuItem';
import Select from '@mui/material/Select';
import Stack from '@mui/material/Stack';

export default function ProjectSettings() {
  const [visibility, setVisibility] = useState('private');
  const [archived, setArchived] = useState(false);

  return (
    <Stack spacing={2}>
      <Select
        value={visibility}
        onChange={(event) => setVisibility(event.target.value)}
        aria-label="Project visibility"
      >
        <MenuItem value="private">Private</MenuItem>
        <MenuItem value="public">Public</MenuItem>
      </Select>
      <FormControlLabel
        label="Archived"
        control={
          <Checkbox
            checked={archived}
            onChange={(event) => setArchived(event.target.checked)}
          />
        }
      />
    </Stack>
  );
}
~~~

For grouped fields, use the corresponding FormControl, InputLabel, FormGroup, or RadioGroup components so each control has a clear label and purpose.

## Choose controlled or uncontrolled state

A controlled component uses a React prop such as <code>value</code>, <code>checked</code>, or <code>open</code>, with a callback that updates state. This is useful when the application must validate, submit, share, or reset the value.

An uncontrolled component keeps its own current value and can receive an initial value through <code>defaultValue</code> or <code>defaultChecked</code>. This can be enough for a small form that does not need to react to each keystroke.

Do not provide both a controlled and uncontrolled value for the same field. Keep a field in one mode for its entire lifetime.

## Keep state simple

Store the smallest set of values needed to describe the screen. Compute values that can be derived from existing state instead of keeping duplicate state that can become inconsistent.

When rendering arrays of options, give each child a stable key. Update arrays and objects by creating a new value instead of mutating the current state.

## Practice questions

1. What role does a Material UI component play when React owns the state?
2. What makes a TextField controlled?
3. Which event property contains the new text field value?
4. Which Checkbox event property contains its checked state?
5. When is controlled state useful?
6. What is an uncontrolled field's initial value prop?
7. Why should a field not switch between controlled and uncontrolled modes?
8. Why should derived values usually be calculated instead of stored twice?

## References

- [React state](https://react.dev/learn/state-a-components-memory)
- [React input components](https://react.dev/reference/react-dom/components/input)
- [Text Field](https://mui.com/material-ui/react-text-field/)
- [Select](https://mui.com/material-ui/react-select/)
- [Checkbox](https://mui.com/material-ui/react-checkbox/)