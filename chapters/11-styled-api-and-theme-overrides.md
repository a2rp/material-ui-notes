# 11. The styled API and theme overrides

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: The sx prop and responsive styles](./10-sx-prop-and-responsive-styles.md) | [Notes index](../README.md) | [Next: Responsive layouts and breakpoints](./12-responsive-layouts-and-breakpoints.md) |

## Pick a styling scope

Material UI offers several styling tools. Choose the narrowest tool that matches the reuse:

| Need | Useful choice |
| --- | --- |
| One adjustment on one instance | <code>sx</code> |
| Reusable component styles | <code>styled</code> |
| Consistent defaults across the app | Theme component configuration |
| Broad rules for plain HTML elements | CSS or <code>GlobalStyles</code> |

## Create a reusable styled component

Use the <code>styled</code> utility when a component's styling is repeated or depends on the theme:

~~~jsx
import { styled } from '@mui/material/styles';

const InfoPanel = styled('section')(({ theme }) => ({
  padding: theme.spacing(2),
  color: theme.palette.text.primary,
  backgroundColor: theme.palette.background.paper,
  border: '1px solid',
  borderColor: theme.palette.divider,
  borderRadius: theme.shape.borderRadius,
}));

export default function Summary() {
  return <InfoPanel>Shared information panel</InfoPanel>;
}
~~~

The callback receives the active theme, so the component follows palette, spacing, and shape changes instead of hard-coding each value.

## Handle custom styling props

A styling-only prop should not accidentally become an invalid HTML attribute. Filter it when creating a styled native element:

~~~jsx
import { styled } from '@mui/material/styles';

const Notice = styled('aside', {
  shouldForwardProp: (prop) => prop !== 'emphasized',
})(({ theme, emphasized }) => ({
  padding: theme.spacing(2),
  borderLeftWidth: 4,
  borderLeftStyle: 'solid',
  borderLeftColor: theme.palette.primary.main,
  fontWeight: emphasized ? 700 : 400,
}));

export default function ExampleNotice() {
  return <Notice emphasized>Important information</Notice>;
}
~~~

If a custom component wraps another Material UI component, forward the documented props that callers need, including <code>className</code> and <code>sx</code> when appropriate.

## Set defaults and overrides in the theme

Theme component configuration applies across the application:

~~~jsx
import { createTheme } from '@mui/material/styles';

const theme = createTheme({
  components: {
    MuiButton: {
      defaultProps: {
        disableElevation: true,
      },
      styleOverrides: {
        root: {
          borderRadius: 10,
          textTransform: 'none',
        },
      },
    },
  },
});

export default theme;
~~~

Use <code>defaultProps</code> for defaults and <code>styleOverrides</code> for shared visual rules. A default still allows a component instance to provide its own supported prop value.

## Target a public slot class

For a small nested style, use a documented global slot class rather than the generated hash-prefixed class:

~~~jsx
<Button
  startIcon={<SaveIcon />}
  sx={{
    '& .MuiButton-startIcon': {
      marginRight: 1,
    },
  }}
>
  Save
</Button>
~~~

The stable class describes a component slot. Generated class names can change between builds. If the same nested rule appears in many places, move it to a reusable component or the theme.

## Keep large customizations local

A long theme object can become hard to understand and may include styles for components the application never uses. For a substantially custom control, create an application component that owns its behavior and styles instead of placing every detail in a global override.

## Practice questions

1. Which styling tool suits one local adjustment?
2. When is <code>styled</code> useful?
3. Where can a reusable styled component read palette and spacing values?
4. What does <code>shouldForwardProp</code> protect against?
5. Where should application-wide Button defaults be configured?
6. What is the purpose of <code>styleOverrides</code>?
7. Why should a generated hash-prefixed class not be targeted?
8. Why can a large global theme override become difficult to maintain?

## References

- [How to customize](https://mui.com/material-ui/customization/how-to-customize/)
- [Themed components](https://mui.com/material-ui/customization/theme-components/)
- [The styled utility](https://mui.com/system/styled/)
- [Creating themed components](https://mui.com/material-ui/customization/creating-themed-components/)