# 6. Dialogs, menus, and feedback

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Forms and input controls](./05-forms-and-input-controls.md) | [Notes index](../README.md) | [Next: Lists, tables, and Data Grid](./07-lists-tables-and-data-grid.md) |

## Show a temporary message

Use Alert to communicate a result or important state. Use Snackbar when the message should appear temporarily without moving the page content:

~~~jsx
import { useState } from 'react';
import Alert from '@mui/material/Alert';
import Button from '@mui/material/Button';
import Snackbar from '@mui/material/Snackbar';

export default function SaveFeedback() {
  const [open, setOpen] = useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)}>Save</Button>
      <Snackbar
        open={open}
        autoHideDuration={4000}
        onClose={() => setOpen(false)}
      >
        <Alert
          severity="success"
          variant="filled"
          onClose={() => setOpen(false)}
        >
          Changes saved.
        </Alert>
      </Snackbar>
    </>
  );
}
~~~

Use a clear, short message. A snackbar should not be the only place where important information appears, because it disappears. Use <code>severity</code> to indicate success, information, warning, or error.

## Confirm a consequential action

A Dialog is appropriate when a person needs to read information or confirm a decision before continuing. Give it a title and explain what each action will do:

~~~jsx
import { useState } from 'react';
import Button from '@mui/material/Button';
import Dialog from '@mui/material/Dialog';
import DialogActions from '@mui/material/DialogActions';
import DialogContent from '@mui/material/DialogContent';
import DialogContentText from '@mui/material/DialogContentText';
import DialogTitle from '@mui/material/DialogTitle';

export default function DeleteConfirmation() {
  const [open, setOpen] = useState(false);

  function closeDialog() {
    setOpen(false);
  }

  return (
    <>
      <Button color="error" onClick={() => setOpen(true)}>
        Delete project
      </Button>
      <Dialog open={open} onClose={closeDialog}>
        <DialogTitle>Delete this project?</DialogTitle>
        <DialogContent>
          <DialogContentText>
            This removes the project from your list. You cannot undo this action.
          </DialogContentText>
        </DialogContent>
        <DialogActions>
          <Button onClick={closeDialog}>Cancel</Button>
          <Button color="error" onClick={closeDialog} autoFocus>
            Delete
          </Button>
        </DialogActions>
      </Dialog>
    </>
  );
}
~~~

This example demonstrates the confirmation interface. A real application must call its delete operation from the confirmed action and handle errors before showing success.

## Open an anchored menu

Menu is connected to a button and appears next to that button. Keep the state of the anchor element so the menu can be positioned correctly:

~~~jsx
import { useState } from 'react';
import Button from '@mui/material/Button';
import Menu from '@mui/material/Menu';
import MenuItem from '@mui/material/MenuItem';

export default function ProjectMenu() {
  const [anchorEl, setAnchorEl] = useState(null);
  const open = Boolean(anchorEl);

  function closeMenu() {
    setAnchorEl(null);
  }

  return (
    <>
      <Button
        aria-controls={open ? 'project-menu' : undefined}
        aria-expanded={open ? 'true' : undefined}
        aria-haspopup="true"
        onClick={(event) => setAnchorEl(event.currentTarget)}
      >
        Project actions
      </Button>
      <Menu
        id="project-menu"
        anchorEl={anchorEl}
        open={open}
        onClose={closeMenu}
      >
        <MenuItem onClick={closeMenu}>Rename</MenuItem>
        <MenuItem onClick={closeMenu}>Archive</MenuItem>
      </Menu>
    </>
  );
}
~~~

Menu handles common keyboard behavior such as moving between menu items and closing with Escape. Use it for a small set of contextual actions. For a persistent navigation area, use a navigation component instead.

## Preserve focus and context

Dialogs and menus manage focus as they open and close. Keep their built-in focus behavior unless there is a specific tested reason to change it. Closing should return a person to the control that opened the surface. Use visible labels and concise action names so the choice remains clear.

## Practice questions

1. When is Snackbar useful?
2. Why should important information not appear only in a temporary Snackbar?
3. What does Alert severity communicate?
4. Which component can request confirmation before an action?
5. What should a confirmation dialog explain?
6. What does Menu use to decide where it opens?
7. Why should a menu-opening button expose its expanded state?
8. Where should focus normally return when a dialog or menu closes?

## References

- [Alert](https://mui.com/material-ui/react-alert/)
- [Snackbar](https://mui.com/material-ui/react-snackbar/)
- [Dialog](https://mui.com/material-ui/react-dialog/)
- [Menu](https://mui.com/material-ui/react-menu/)