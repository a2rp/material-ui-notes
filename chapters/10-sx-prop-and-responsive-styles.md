# 10. The sx prop and responsive styles

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Themes, palettes, and color schemes](./09-themes-palettes-and-color-schemes.md) | [Notes index](../README.md) | [Next: The styled API and theme overrides](./11-styled-api-and-theme-overrides.md) |

## Make a local style adjustment

The <code>sx</code> prop applies styles to one component and can read theme values. It supports regular CSS properties plus theme-aware shorthand properties:

~~~jsx
import Box from '@mui/material/Box';
import Typography from '@mui/material/Typography';

export default function NoteSummary() {
  return (
    <Box
      sx={{
        p: 2,
        border: 1,
        borderColor: 'divider',
        borderRadius: 2,
        bgcolor: 'background.paper',
      }}
    >
      <Typography color="text.secondary">
        A bordered summary panel with spacing from the theme.
      </Typography>
    </Box>
  );
}
~~~

Here <code>p</code> reads from the theme spacing scale, <code>borderColor</code> reads from the palette, and <code>borderRadius</code> uses a theme shape value. A numeric spacing value is not always the same as a raw CSS pixel count.

## Set styles by breakpoint

Responsive values can use breakpoint keys. A value applies at its breakpoint and above until a later value overrides it:

~~~jsx
import Box from '@mui/material/Box';

export default function ResponsivePanel() {
  return (
    <Box
      sx={{
        display: { xs: 'block', md: 'flex' },
        gap: { xs: 1, md: 3 },
        p: { xs: 2, md: 4 },
      }}
    >
      <Box>Navigation</Box>
      <Box sx={{ flex: 1 }}>Main content</Box>
    </Box>
  );
}
~~~

The default breakpoint names are <code>xs</code>, <code>sm</code>, <code>md</code>, <code>lg</code>, and <code>xl</code>. A theme can customize those values, so use the project theme as the source of truth.

## Use responsive arrays carefully

Responsive properties can also be written as arrays in breakpoint order. The keys are easier to read when there are several values, so prefer an object for complex styles:

~~~jsx
<Box sx={{ width: { xs: '100%', sm: '80%', md: 640 } }}>
  Content
</Box>
~~~

Start with the narrow layout and add changes at wider breakpoints. This keeps the default experience usable on small screens.

## Keep styling in the right place

Use <code>sx</code> for a small local adjustment. Move repeated styling into a reusable component or the <code>styled</code> utility. Put design-wide defaults in the theme. Use CSS files for larger static styles and selectors that are easier to understand as CSS.

Avoid long conditional styling expressions inside the JSX. Extract a value or component when the conditions obscure what the interface does.

For visual layout changes, CSS breakpoints are usually enough. Use the <code>useMediaQuery</code> hook when the JavaScript behavior itself needs to change with the viewport, not just the appearance.

## Practice questions

1. What is the <code>sx</code> prop useful for?
2. How does a theme-aware color value differ from a raw color literal?
3. What does the <code>p</code> shorthand use?
4. How do responsive object values work across breakpoints?
5. What are the default breakpoint names?
6. Why should responsive layouts begin with the narrow layout?
7. When might a reusable styled component be better than a long <code>sx</code> expression?
8. When is <code>useMediaQuery</code> needed instead of a CSS breakpoint?

## References

- [The sx prop](https://mui.com/system/getting-started/the-sx-prop/)
- [System properties](https://mui.com/system/getting-started/usage/#system-properties)
- [Breakpoints](https://mui.com/material-ui/customization/breakpoints/)
- [useMediaQuery](https://mui.com/material-ui/react-use-media-query/)