# 8. Navigation and application shells

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Lists, tables, and Data Grid](./07-lists-tables-and-data-grid.md) | [Notes index](../README.md) | [Next: Themes, palettes, and color schemes](./09-themes-palettes-and-color-schemes.md) |

## Build a top application bar

AppBar and Toolbar provide a common top-level shell. Keep page navigation in a semantic navigation region and use links for destinations:

~~~jsx
import AppBar from '@mui/material/AppBar';
import Button from '@mui/material/Button';
import Toolbar from '@mui/material/Toolbar';
import Typography from '@mui/material/Typography';

export default function TopBar() {
  return (
    <AppBar position="static">
      <Toolbar>
        <Typography component="span" variant="h6" sx={{ flexGrow: 1 }}>
          Study space
        </Typography>
        <nav aria-label="Main navigation">
          <Button color="inherit" href="/notes">Notes</Button>
          <Button color="inherit" href="/about">About</Button>
        </nav>
      </Toolbar>
    </AppBar>
  );
}
~~~

The Toolbar provides the bar's layout and vertical alignment. Use <code>position="static"</code> when the bar should remain in document flow. A fixed bar is removed from normal flow, so the page may need spacing beneath it.

## Use a Drawer for a navigation list

A permanent Drawer suits navigation that remains visible in a wide layout. A temporary Drawer is typically controlled by React state on a small screen:

~~~jsx
import { useState } from 'react';
import Box from '@mui/material/Box';
import Button from '@mui/material/Button';
import Drawer from '@mui/material/Drawer';
import List from '@mui/material/List';
import ListItemButton from '@mui/material/ListItemButton';
import ListItemText from '@mui/material/ListItemText';

export default function MobileNavigation() {
  const [open, setOpen] = useState(false);

  function closeDrawer() {
    setOpen(false);
  }

  return (
    <>
      <Button aria-expanded={open} onClick={() => setOpen(true)}>
        Open navigation
      </Button>
      <Drawer anchor="left" open={open} onClose={closeDrawer}>
        <Box sx={{ width: 280 }} role="presentation">
          <nav aria-label="Section navigation">
            <List>
              <ListItemButton component="a" href="/notes" onClick={closeDrawer}>
                <ListItemText primary="Notes" />
              </ListItemButton>
              <ListItemButton component="a" href="/projects" onClick={closeDrawer}>
                <ListItemText primary="Projects" />
              </ListItemButton>
            </List>
          </nav>
        </Box>
      </Drawer>
    </>
  );
}
~~~

The temporary Drawer closes on backdrop interaction or Escape. Close it after selecting a destination so the new page is visible.

## Use Tabs for local views

Tabs switch between related views within the same section. Connect each tab to the content it controls, and expose a label for the set:

~~~jsx
import { useState } from 'react';
import Box from '@mui/material/Box';
import Tab from '@mui/material/Tab';
import Tabs from '@mui/material/Tabs';
import Typography from '@mui/material/Typography';

export default function NoteViews() {
  const [activeTab, setActiveTab] = useState('recent');

  return (
    <Box>
      <Tabs
        aria-label="Note views"
        value={activeTab}
        onChange={(event, nextTab) => setActiveTab(nextTab)}
      >
        <Tab label="Recent" value="recent" />
        <Tab label="Saved" value="saved" />
      </Tabs>
      <Typography role="tabpanel">
        {activeTab === 'recent' ? 'Recently viewed notes' : 'Saved notes'}
      </Typography>
    </Box>
  );
}
~~~

For a complete tabs interface, connect each tab and panel with matching IDs and accessibility attributes. Use navigation links instead of tabs when the items lead to separate pages rather than changing a local view.

## Show hierarchy with breadcrumbs

Breadcrumbs show a page's position inside a hierarchy. Include a label for the navigation and make the current page clear:

~~~jsx
import Breadcrumbs from '@mui/material/Breadcrumbs';
import Link from '@mui/material/Link';
import Typography from '@mui/material/Typography';

export default function PagePath() {
  return (
    <Breadcrumbs aria-label="breadcrumb">
      <Link underline="hover" color="inherit" href="/">Home</Link>
      <Link underline="hover" color="inherit" href="/notes">Notes</Link>
      <Typography color="text.primary">Components</Typography>
    </Breadcrumbs>
  );
}
~~~

## Practice questions

1. What do AppBar and Toolbar provide?
2. Which Drawer variant typically fits a menu opened temporarily on mobile?
3. How can a person close a temporary Drawer without choosing a link?
4. When are Tabs appropriate?
5. When should page destinations use links instead of Tabs?
6. What do breadcrumbs communicate?
7. Why should navigation have an accessible label?
8. What layout issue can a fixed AppBar cause?

## References

- [App Bar](https://mui.com/material-ui/react-app-bar/)
- [Drawer](https://mui.com/material-ui/react-drawer/)
- [Tabs](https://mui.com/material-ui/react-tabs/)
- [Breadcrumbs](https://mui.com/material-ui/react-breadcrumbs/)
- [Material UI routing integration](https://mui.com/material-ui/integrations/routing/)