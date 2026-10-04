# 5. Forms and input controls

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Buttons, links, and icons](./04-buttons-links-and-icons.md) | [Notes index](../README.md) | [Next: Dialogs, menus, and feedback](./06-dialogs-menus-and-feedback.md) |

## Build a text field

TextField combines a label, input, and helper text for common form fields:

~~~jsx
import TextField from '@mui/material/TextField';

export default function EmailField() {
  return (
    <TextField
      autoComplete="email"
      fullWidth
      helperText="We will use this address for account updates."
      label="Email address"
      name="email"
      type="email"
    />
  );
}
~~~

Give every input a visible label. Use helper text for instructions that help a person enter the value correctly. Set <code>required</code> when the field is required, and use <code>error</code> with clear helper text when validation fails.

## Controlled values with React

A controlled input receives its value from React state and updates that state from its event handler:

~~~jsx
import { useState } from 'react';
import TextField from '@mui/material/TextField';

export default function NameField() {
  const [name, setName] = useState('');

  return (
    <TextField
      label="Name"
      value={name}
      onChange={(event) => setName(event.target.value)}
    />
  );
}
~~~

Do not switch one input between a controlled <code>value</code> and an uncontrolled <code>defaultValue</code>. Choose one approach for its lifetime.

## Select a value

Use a labeled Select when the person should choose one option from a small, known set:

~~~jsx
import FormControl from '@mui/material/FormControl';
import InputLabel from '@mui/material/InputLabel';
import MenuItem from '@mui/material/MenuItem';
import Select from '@mui/material/Select';

export default function LanguageField() {
  return (
    <FormControl fullWidth>
      <InputLabel id="language-label">Language</InputLabel>
      <Select
        defaultValue="javascript"
        label="Language"
        labelId="language-label"
        name="language"
      >
        <MenuItem value="javascript">JavaScript</MenuItem>
        <MenuItem value="python">Python</MenuItem>
        <MenuItem value="java">Java</MenuItem>
      </Select>
    </FormControl>
  );
}
~~~

The label ID connects the visible label to the Select. For a long searchable list, a select menu may not be the right control. Consider an autocomplete component when its interaction matches the task.

## Checkbox, radio, and switch

A checkbox represents an independent choice. Radio buttons represent one choice from a group. A switch represents an on or off setting.

~~~jsx
import Checkbox from '@mui/material/Checkbox';
import FormControlLabel from '@mui/material/FormControlLabel';
import FormGroup from '@mui/material/FormGroup';
import Radio from '@mui/material/Radio';
import RadioGroup from '@mui/material/RadioGroup';
import Switch from '@mui/material/Switch';

export default function Preferences() {
  return (
    <>
      <FormGroup>
        <FormControlLabel
          control={<Checkbox name="updates" />}
          label="Email me product updates"
        />
        <FormControlLabel
          control={<Switch name="darkMode" />}
          label="Use dark mode"
        />
      </FormGroup>

      <RadioGroup defaultValue="email" name="contact-method">
        <FormControlLabel value="email" control={<Radio />} label="Email" />
        <FormControlLabel value="phone" control={<Radio />} label="Phone" />
      </RadioGroup>
    </>
  );
}
~~~

Use <code>FormControlLabel</code> to associate a visible label with each control. Keep labels specific enough that the purpose remains clear when the control is read out of context.

## Validate before submitting

Browser validation can catch simple mistakes, but the server must validate submitted data too. Client-side checks improve feedback; they do not make submitted values trustworthy.

A form submit handler can stop the browser's default page navigation and then perform application validation:

~~~jsx
function handleSubmit(event) {
  event.preventDefault();

  if (!email.includes('@')) {
    setError('Enter a valid email address.');
    return;
  }

  setError('');
  saveEmail(email);
}
~~~

Display an error beside the field, and explain how to fix it. Do not rely on color alone to communicate that a value is invalid.

## Practice questions

1. Which component combines a label and input for a common text field?
2. Why should an input have a visible label?
3. What makes a React input controlled?
4. Should one input switch between <code>value</code> and <code>defaultValue</code>?
5. What connects the visible Select label to the control?
6. Which input suits multiple independent choices?
7. Which input suits one choice from a group?
8. Why must the server validate form data even when the browser already checked it?

## References

- [Text Field](https://mui.com/material-ui/react-text-field/)
- [Select](https://mui.com/material-ui/react-select/)
- [Checkbox](https://mui.com/material-ui/react-checkbox/)
- [Radio Group](https://mui.com/material-ui/react-radio-button/)
- [Switch](https://mui.com/material-ui/react-switch/)
- [React input components](https://react.dev/reference/react-dom/components/input)