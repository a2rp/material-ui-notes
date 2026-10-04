# 12. Responsive layouts and breakpoints

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: The styled API and theme overrides](./11-styled-api-and-theme-overrides.md) | [Notes index](../README.md) | [Next: Accessibility and keyboard navigation](./13-accessibility-and-keyboard-navigation.md) |

## Start with a small screen

A responsive layout adapts as the available space changes. Begin with a narrow layout, then add changes where the content needs more room. Use <code>Container</code> to limit the reading width, <code>Stack</code> for a simple row or column, and <code>Grid</code> when content needs proportional columns.

## Use the current Grid API

The current Material UI Grid uses the <code>size</code> prop for column widths. The default grid has 12 columns:

~~~jsx
import Grid from '@mui/material/Grid';
import Paper from '@mui/material/Paper';
import Typography from '@mui/material/Typography';

export default function ProjectLayout() {
  return (
    <Grid container spacing={2}>
      <Grid size={{ xs: 12, md: 4 }}>
        <Paper sx={{ p: 2 }}>
          <Typography component="h2" variant="h6">Navigation</Typography>
        </Paper>
      </Grid>
      <Grid size={{ xs: 12, md: 8 }}>
        <Paper sx={{ p: 2 }}>
          <Typography component="h2" variant="h6">Main content</Typography>
        </Paper>
      </Grid>
    </Grid>
  );
}
~~~

At the narrow <code>xs</code> breakpoint, both regions use all 12 columns and stack. At <code>md</code> and wider, navigation uses 4 columns and the main area uses 8. Grid spacing follows the theme spacing scale.

Older examples may use <code>item</code> and breakpoint props directly on Grid children. Use the API for the installed Material UI version when adapting older code.

## Use CSS Grid for two-dimensional placement

Material UI Grid is based on flexbox and is useful for responsive columns. When the layout needs explicit rows, named areas, or automatic placement, CSS Grid is a better fit:

~~~jsx
import Box from '@mui/material/Box';

export default function TileLayout({ children }) {
  return (
    <Box
      sx={{
        display: 'grid',
        gridTemplateColumns: {
          xs: '1fr',
          sm: 'repeat(2, minmax(0, 1fr))',
          lg: 'repeat(3, minmax(0, 1fr))',
        },
        gap: 2,
      }}
    >
      {children}
    </Box>
  );
}
~~~

Use <code>minmax(0, 1fr)</code> when long content should be allowed to shrink instead of forcing a column wider than its container.

## Change behavior at a breakpoint

Use the <code>useMediaQuery</code> hook when JavaScript behavior needs to change, such as selecting a temporary or permanent Drawer. For appearance alone, prefer CSS through <code>sx</code> so the browser can adapt the layout without extra React state:

~~~jsx
import useMediaQuery from '@mui/material/useMediaQuery';
import { useTheme } from '@mui/material/styles';

export default function useWideLayout() {
  const theme = useTheme();
  return useMediaQuery(theme.breakpoints.up('md'));
}
~~~

The hook returns a boolean. On server-rendered pages, the server does not know the actual viewport width, so test how responsive behavior is initialized to avoid a visual mismatch after hydration.

## Keep content readable

Do not use breakpoints only because a familiar screen width has been reached. Add a breakpoint when the content no longer fits or the visual hierarchy needs to change. Test long labels, keyboard focus, zoom, and narrow screens, not just the default desktop size.

## Practice questions

1. What does a breakpoint represent?
2. How many columns does the default Material UI Grid use?
3. Which prop sets a Grid child's width in the current API?
4. How does the example change at the <code>md</code> breakpoint?
5. When is CSS Grid more suitable than Material UI Grid?
6. Why can <code>minmax(0, 1fr)</code> help with long content?
7. When should <code>useMediaQuery</code> be used?
8. Why should a server-rendered page test responsive initialization?

## References

- [Grid](https://mui.com/material-ui/react-grid/)
- [Container](https://mui.com/material-ui/react-container/)
- [Breakpoints](https://mui.com/material-ui/customization/breakpoints/)
- [useMediaQuery](https://mui.com/material-ui/react-use-media-query/)
- [CSS Grid guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)