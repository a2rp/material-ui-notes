# 16. Testing and production patterns

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Performance and server rendering](./15-performance-and-server-rendering.md) | [Notes index](../README.md) | [Next: All code samples](./98-all-code-samples.md) |

## Test what a person can use

Test visible behavior through roles, labels, and interactions. Avoid coupling tests to generated class names or private DOM structure that can change between library versions.

This Vitest and Testing Library example checks that a button calls the action passed to it:

~~~jsx
import { describe, expect, it, vi } from 'vitest';
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Button from '@mui/material/Button';

function SaveAction({ onSave }) {
  return <Button onClick={onSave}>Save project</Button>;
}

describe('SaveAction', () => {
  it('calls the supplied action when activated', async () => {
    const user = userEvent.setup();
    const onSave = vi.fn();

    render(<SaveAction onSave={onSave} />);

    await user.click(screen.getByRole('button', { name: 'Save project' }));

    expect(onSave).toHaveBeenCalledTimes(1);
  });
});
~~~

The test finds the button by its role and accessible name, then interacts with it as a person would. Keep business logic assertions separate from checks about exact CSS output.

## Test form feedback

Check that fields have labels and that validation feedback appears when expected. Test an accessible result rather than only checking that an internal error flag changed.

~~~jsx
expect(screen.getByRole('textbox', { name: 'Email address' })).toBeVisible();
expect(screen.getByText('Enter a valid email address.')).toBeVisible();
~~~

For a Select, dialog, menu, or tabs, query the element by its role and accessible name. Use the keyboard in at least one test for an interaction that supports keyboard use.

## Provide a theme when needed

Components that depend on a custom application theme should be rendered with the same provider used by the application. Keep test helpers small and use a real theme so the test exercises the intended setup.

Prefer testing that a theme-dependent behavior is visible, such as a component label or interaction. Avoid asserting a generated Emotion class name, because that couples the test to styling output.

## Check the full production experience

Before release, verify the production build and test the application at realistic viewport sizes. Confirm that:

- Labels and accessible names are present
- Focus indicators remain visible
- Dialogs, menus, and tabs work from the keyboard
- Loading, empty, success, and error states are understandable
- The theme is consistent across pages
- Fonts and styles load correctly on a fresh page request
- Large lists remain usable at expected data sizes
- No unsupported props or console warnings appear

For an app with server rendering, check both the initial HTML response and the hydrated page. Confirm there is no missing-style flash and no mismatch between the server and browser output.

## Practice questions

1. What should a component test focus on?
2. Why is querying by role and accessible name useful?
3. What does <code>userEvent</code> help a test simulate?
4. Why should tests avoid generated class names?
5. When should a test provide the application theme?
6. What interaction should be checked by keyboard?
7. What should be verified for a server-rendered page?
8. Why should the production build be checked at realistic viewport sizes?

## References

- [Material UI testing](https://mui.com/material-ui/guides/testing/)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Testing Library user-event](https://testing-library.com/docs/user-event/intro/)
- [Vitest](https://vitest.dev/guide/)