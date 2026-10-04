# 98. All code samples

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Testing and production patterns](./16-testing-and-production-patterns.md) | [Notes index](../README.md) | [Next: Complete questions and answers](./99-complete-q-and-a.md) |

## Getting started with Material UI

Source: [Open chapter](./01-getting-started-with-material-ui.md)

### Example 1

~~~~sh
npm install @mui/material @emotion/react @emotion/styled
~~~~

### Example 2

~~~~sh
npm install @fontsource/roboto
~~~~

### Example 3

~~~~sh
npm install @mui/icons-material
~~~~

### Example 4

~~~~jsx
import Button from '@mui/material/Button';

export default function Welcome() {
  return (
    <main>
      <h1>My first Material UI component</h1>
      <Button
        variant="contained"
        onClick={() => window.alert('The button works')}
      >
        Try the button
      </Button>
    </main>
  );
}
~~~~

### Example 5

~~~~jsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import CssBaseline from '@mui/material/CssBaseline';
import '@fontsource/roboto/400.css';
import '@fontsource/roboto/500.css';
import App from './App.jsx';

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <CssBaseline />
    <App />
  </StrictMode>
);
~~~~

### Example 6

~~~~html
<meta name="viewport" content="initial-scale=1, width=device-width" />
~~~~

### Example 7

~~~~jsx
import Button from '@mui/material/Button';
import { Stack, Typography } from '@mui/material';
~~~~

## Components, props, and composition

Source: [Open chapter](./02-components-props-and-composition.md)

### Example 1

~~~~jsx
import Alert from '@mui/material/Alert';

export default function SaveMessage() {
  return <Alert severity="success">Changes saved</Alert>;
}
~~~~

### Example 2

~~~~jsx
import Button from '@mui/material/Button';
import Card from '@mui/material/Card';
import CardActions from '@mui/material/CardActions';
import CardContent from '@mui/material/CardContent';
import Typography from '@mui/material/Typography';

export default function ProjectCard() {
  return (
    <Card>
      <CardContent>
        <Typography variant="h6" component="h2">
          Linux notes
        </Typography>
        <Typography color="text.secondary">
          A practical reference for everyday commands.
        </Typography>
      </CardContent>
      <CardActions>
        <Button href="/notes">Open notes</Button>
      </CardActions>
    </Card>
  );
}
~~~~

### Example 3

~~~~jsx
import Button from '@mui/material/Button';
import Typography from '@mui/material/Typography';

export default function PageHeading() {
  return (
    <>
      <Typography variant="h4" component="h1">
        Projects
      </Typography>
      <Button href="/projects">Browse projects</Button>
    </>
  );
}
~~~~

### Example 4

~~~~jsx
import Button from '@mui/material/Button';

export function PrimaryAction({ children, ...buttonProps }) {
  return (
    <Button variant="contained" {...buttonProps}>
      {children}
    </Button>
  );
}
~~~~

## Typography, surfaces, and layout

Source: [Open chapter](./03-typography-surfaces-and-layout.md)

### Example 1

~~~~jsx
import Typography from '@mui/material/Typography';

export default function SectionTitle() {
  return (
    <header>
      <Typography variant="h1" component="h1">
        Project notes
      </Typography>
      <Typography variant="body1" component="p">
        Practical examples for building React interfaces.
      </Typography>
    </header>
  );
}
~~~~

### Example 2

~~~~jsx
import Button from '@mui/material/Button';
import Container from '@mui/material/Container';
import Stack from '@mui/material/Stack';
import Typography from '@mui/material/Typography';

export default function NotesHeader() {
  return (
    <Container maxWidth="md">
      <Stack spacing={2}>
        <Typography variant="h1" component="h1">
          Material UI notes
        </Typography>
        <Typography color="text.secondary">
          Learn components by building small interface sections.
        </Typography>
        <Button variant="contained">Browse chapters</Button>
      </Stack>
    </Container>
  );
}
~~~~

### Example 3

~~~~jsx
import Card from '@mui/material/Card';
import CardContent from '@mui/material/CardContent';
import Typography from '@mui/material/Typography';

export default function NoteCard() {
  return (
    <Card component="article">
      <CardContent>
        <Typography variant="h2" component="h2">
          Layout basics
        </Typography>
        <Typography color="text.secondary">
          Use containers and stacks to establish a clear reading width.
        </Typography>
      </CardContent>
    </Card>
  );
}
~~~~

### Example 4

~~~~jsx
import Divider from '@mui/material/Divider';
import Stack from '@mui/material/Stack';
import Typography from '@mui/material/Typography';

export default function TopicList() {
  return (
    <Stack divider={<Divider flexItem />} spacing={2}>
      <Typography component="h2" variant="h6">Components</Typography>
      <Typography component="h2" variant="h6">Theming</Typography>
      <Typography component="h2" variant="h6">Accessibility</Typography>
    </Stack>
  );
}
~~~~

## Buttons, links, and icons

Source: [Open chapter](./04-buttons-links-and-icons.md)

### Example 1

~~~~jsx
import Button from '@mui/material/Button';
import Stack from '@mui/material/Stack';

export default function ButtonExamples() {
  return (
    <Stack direction="row" spacing={2}>
      <Button variant="text">Text</Button>
      <Button variant="outlined">Outlined</Button>
      <Button variant="contained">Contained</Button>
    </Stack>
  );
}
~~~~

### Example 2

~~~~jsx
<Button color="success" size="large" variant="contained">
  Save changes
</Button>
~~~~

### Example 3

~~~~jsx
<Button href="/settings" variant="outlined">
  Open settings
</Button>
~~~~

### Example 4

~~~~jsx
import Link from '@mui/material/Link';

export default function HelpLink() {
  return (
    <Link href="/help" underline="hover">
      Read help
    </Link>
  );
}
~~~~

### Example 5

~~~~jsx
import AddIcon from '@mui/icons-material/Add';
import Button from '@mui/material/Button';

export default function AddButton() {
  return (
    <Button startIcon={<AddIcon />} variant="contained">
      Add project
    </Button>
  );
}
~~~~

### Example 6

~~~~jsx
import DeleteIcon from '@mui/icons-material/Delete';
import IconButton from '@mui/material/IconButton';
import Tooltip from '@mui/material/Tooltip';

export default function DeleteButton() {
  return (
    <Tooltip title="Delete project">
      <IconButton aria-label="Delete project" color="error">
        <DeleteIcon />
      </IconButton>
    </Tooltip>
  );
}
~~~~

### Example 7

~~~~jsx
import Button from '@mui/material/Button';
import ButtonGroup from '@mui/material/ButtonGroup';

export default function ViewChoices() {
  return (
    <ButtonGroup aria-label="Choose a view">
      <Button>List</Button>
      <Button>Grid</Button>
    </ButtonGroup>
  );
}
~~~~

## Forms and input controls

Source: [Open chapter](./05-forms-and-input-controls.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
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
~~~~

### Example 4

~~~~jsx
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
~~~~

### Example 5

~~~~jsx
import { useState } from 'react';
import Alert from '@mui/material/Alert';
import Button from '@mui/material/Button';
import TextField from '@mui/material/TextField';

export default function EmailForm() {
  const [email, setEmail] = useState('');
  const [error, setError] = useState('');
  const [saved, setSaved] = useState(false);

  function handleSubmit(event) {
    event.preventDefault();

    if (!email.includes('@')) {
      setError('Enter a valid email address.');
      setSaved(false);
      return;
    }

    setError('');
    setSaved(true);
  }

  return (
    <form onSubmit={handleSubmit}>
      <TextField
        autoComplete="email"
        error={Boolean(error)}
        helperText={error || 'Enter an address we can contact.'}
        label="Email address"
        type="email"
        value={email}
        onChange={(event) => setEmail(event.target.value)}
      />
      <Button type="submit" variant="contained">Save email</Button>
      {saved && <Alert severity="success">Email saved.</Alert>}
    </form>
  );
}
~~~~

## Dialogs, menus, and feedback

Source: [Open chapter](./06-dialogs-menus-and-feedback.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
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
~~~~

## Lists, tables, and Data Grid

Source: [Open chapter](./07-lists-tables-and-data-grid.md)

### Example 1

~~~~jsx
import List from '@mui/material/List';
import ListItem from '@mui/material/ListItem';
import ListItemButton from '@mui/material/ListItemButton';
import ListItemText from '@mui/material/ListItemText';

const topics = ['Components', 'Forms', 'Theming'];

export default function TopicList() {
  return (
    <List aria-label="Study topics">
      {topics.map((topic) => (
        <ListItem key={topic} disablePadding>
          <ListItemButton>
            <ListItemText primary={topic} />
          </ListItemButton>
        </ListItem>
      ))}
    </List>
  );
}
~~~~

### Example 2

~~~~jsx
import Paper from '@mui/material/Paper';
import Table from '@mui/material/Table';
import TableBody from '@mui/material/TableBody';
import TableCell from '@mui/material/TableCell';
import TableContainer from '@mui/material/TableContainer';
import TableHead from '@mui/material/TableHead';
import TableRow from '@mui/material/TableRow';

const rows = [
  { name: 'Components', chapters: 4 },
  { name: 'Theming', chapters: 3 },
];

export default function TopicTable() {
  return (
    <TableContainer component={Paper}>
      <Table aria-label="Notes by topic">
        <TableHead>
          <TableRow>
            <TableCell>Topic</TableCell>
            <TableCell align="right">Chapters</TableCell>
          </TableRow>
        </TableHead>
        <TableBody>
          {rows.map((row) => (
            <TableRow key={row.name}>
              <TableCell component="th" scope="row">{row.name}</TableCell>
              <TableCell align="right">{row.chapters}</TableCell>
            </TableRow>
          ))}
        </TableBody>
      </Table>
    </TableContainer>
  );
}
~~~~

### Example 3

~~~~sh
npm install @mui/x-data-grid
~~~~

### Example 4

~~~~jsx
import { DataGrid } from '@mui/x-data-grid';

const rows = [
  { id: 1, name: 'Buttons', status: 'Complete' },
  { id: 2, name: 'Forms', status: 'In progress' },
];

const columns = [
  { field: 'name', headerName: 'Topic', flex: 1 },
  { field: 'status', headerName: 'Status', flex: 1 },
];

export default function TopicGrid() {
  return (
    <div style={{ height: 360, width: '100%' }}>
      <DataGrid
        rows={rows}
        columns={columns}
        initialState={{
          pagination: { paginationModel: { page: 0, pageSize: 5 } },
        }}
        pageSizeOptions={[5, 10]}
      />
    </div>
  );
}
~~~~

## Navigation and application shells

Source: [Open chapter](./08-navigation-and-application-shells.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
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
        <Tab
          id="note-tab-recent"
          aria-controls="note-panel-recent"
          label="Recent"
          value="recent"
        />
        <Tab
          id="note-tab-saved"
          aria-controls="note-panel-saved"
          label="Saved"
          value="saved"
        />
      </Tabs>
      <Box
        id="note-panel-recent"
        role="tabpanel"
        aria-labelledby="note-tab-recent"
        hidden={activeTab !== 'recent'}
        sx={{ p: 2 }}
      >
        <Typography>Recently viewed notes</Typography>
      </Box>
      <Box
        id="note-panel-saved"
        role="tabpanel"
        aria-labelledby="note-tab-saved"
        hidden={activeTab !== 'saved'}
        sx={{ p: 2 }}
      >
        <Typography>Saved notes</Typography>
      </Box>
    </Box>
  );
}
~~~~

### Example 4

~~~~jsx
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
~~~~

## Themes, palettes, and color schemes

Source: [Open chapter](./09-themes-palettes-and-color-schemes.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
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
~~~~

### Example 4

~~~~jsx
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
~~~~

## The sx prop and responsive styles

Source: [Open chapter](./10-sx-prop-and-responsive-styles.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
<Box sx={{ width: { xs: '100%', sm: '80%', md: 640 } }}>
  Content
</Box>
~~~~

## The styled API and theme overrides

Source: [Open chapter](./11-styled-api-and-theme-overrides.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
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
~~~~

### Example 4

~~~~jsx
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
~~~~

## Responsive layouts and breakpoints

Source: [Open chapter](./12-responsive-layouts-and-breakpoints.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
import useMediaQuery from '@mui/material/useMediaQuery';
import { useTheme } from '@mui/material/styles';

export default function useWideLayout() {
  const theme = useTheme();
  return useMediaQuery(theme.breakpoints.up('md'));
}
~~~~

## Accessibility and keyboard navigation

Source: [Open chapter](./13-accessibility-and-keyboard-navigation.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

### Example 3

~~~~jsx
import IconButton from '@mui/material/IconButton';
import MenuIcon from '@mui/icons-material/Menu';

export default function MenuButton() {
  return (
    <IconButton aria-label="Open navigation">
      <MenuIcon aria-hidden="true" />
    </IconButton>
  );
}
~~~~

## React state and controlled components

Source: [Open chapter](./14-react-state-and-controlled-components.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
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
~~~~

## Performance and server rendering

Source: [Open chapter](./15-performance-and-server-rendering.md)

### Example 1

~~~~jsx
import Button from '@mui/material/Button';
import TextField from '@mui/material/TextField';
import AddIcon from '@mui/icons-material/Add';
~~~~

## Testing and production patterns

Source: [Open chapter](./16-testing-and-production-patterns.md)

### Example 1

~~~~jsx
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
~~~~

### Example 2

~~~~jsx
expect(screen.getByRole('textbox', { name: 'Email address' })).toBeVisible();
expect(screen.getByText('Enter a valid email address.')).toBeVisible();
~~~~
