# 9. Themes, palettes, and color schemes

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Navigation and application shells](./08-navigation-and-application-shells.md) | [Notes index](../README.md) | [Next: The sx prop and responsive styles](./10-sx-prop-and-responsive-styles.md) |

## Create a shared theme

A theme stores design choices that should stay consistent across an application. Use <code>createTheme</code> to define it and <code>ThemeProvider</code> to make it available to descendant components:

~~~jsx
import { createTheme } from '@mui/material/styles';

const theme = createTheme({
  palette: {
    primary: { main: '#174ea6' },
    secondary: { main: '#8a3ffc' },
    background: {
      default: '#f7f8fa',
      paper: '#ffffff',
    },
  },
  typography: {
    fontFamily: 'Roboto, Arial, sans-serif',
  },
  shape: {
    borderRadius: 10,
  },
});

export default theme;
~~~

Wrap the application near its root so pages and shared components use the same values:

~~~jsx
import CssBaseline from '@mui/material/CssBaseline';
import { ThemeProvider } from '@mui/material/styles';
import { createRoot } from 'react-dom/client';
import App from './App.jsx';
import theme from './theme.js';

createRoot(document.getElementById('root')).render(
  <ThemeProvider theme={theme}>
    <CssBaseline />
    <App />
  </ThemeProvider>
);
~~~

The baseline and theme provider solve different problems. The provider shares theme values. <code>CssBaseline</code> applies base styles to the page.

## Use palette roles

Components can request a palette role instead of repeating a raw color:

~~~jsx
import Alert from '@mui/material/Alert';
import Button from '@mui/material/Button';
import Stack from '@mui/material/Stack';

export default function StatusActions() {
  return (
    <Stack spacing={2}>
      <Alert severity="success">Changes saved.</Alert>
      <Button color="primary" variant="contained">Continue</Button>
    </Stack>
  );
}
~~~

The palette includes common roles such as primary, secondary, error, warning, info, success, text, and backgrounds. Use those roles consistently so the same meaning and contrast are preserved across components.

A palette choice alone does not guarantee readable contrast for every custom pairing. Check foreground and background contrast, including hover, disabled, and focus states.

## Support light and dark mode

The palette mode adjusts built-in colors and surfaces. Keep the mode in React state when a person can switch it:

~~~jsx
import { useMemo, useState } from 'react';
import Button from '@mui/material/Button';
import CssBaseline from '@mui/material/CssBaseline';
import { createTheme, ThemeProvider } from '@mui/material/styles';

export default function AppTheme({ children }) {
  const [mode, setMode] = useState('light');
  const theme = useMemo(
    () => createTheme({ palette: { mode } }),
    [mode]
  );

  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <Button onClick={() => setMode(mode === 'light' ? 'dark' : 'light')}>
        Switch color mode
      </Button>
      {children}
    </ThemeProvider>
  );
}
~~~

A complete interface should also persist the choice if needed and consider the operating system preference. Do not create a new theme object on every render when its inputs have not changed.

## Use theme values in components

Material UI components read colors, typography, spacing, shape, and breakpoints from the active theme. Prefer theme values when styling a component so a change to the design system can be applied consistently later.

Global default props and style overrides are also defined through the theme. Use them only for rules that should apply broadly; a one-off adjustment is clearer on the component where it is used.

## Practice questions

1. What does a theme store?
2. Which provider makes the theme available to descendant components?
3. What does <code>CssBaseline</code> do?
4. Why use palette roles instead of repeating raw colors?
5. Which palette setting selects light or dark mode?
6. Does a palette automatically guarantee sufficient text contrast?
7. Why should a theme object avoid being recreated on every render?
8. When should a global theme override be used instead of a local style?

## References

- [Theming](https://mui.com/material-ui/customization/theming/)
- [Palette](https://mui.com/material-ui/customization/palette/)
- [Dark mode](https://mui.com/material-ui/customization/dark-mode/)
- [CssBaseline](https://mui.com/material-ui/react-css-baseline/)
- [ThemeProvider API](https://mui.com/material-ui/customization/theming/#theme-provider)