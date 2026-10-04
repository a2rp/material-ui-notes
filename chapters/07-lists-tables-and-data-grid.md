# 7. Lists, tables, and Data Grid

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Dialogs, menus, and feedback](./06-dialogs-menus-and-feedback.md) | [Notes index](../README.md) | [Next: Navigation and application shells](./08-navigation-and-application-shells.md) |

## Choose a data component

Use a list for related items where each item may contain supporting text or an action. Use a table when the data naturally compares the same fields across rows. Use Data Grid when a larger interactive dataset needs features such as sorting, selection, or pagination.

A semantic table is often the simplest choice for a small, mostly static set of rows. Data Grid is part of MUI X and is installed separately from <code>@mui/material</code>.

## Build a list

Compose a list from list items and give each row a clear primary label:

~~~jsx
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
~~~

Provide a stable React key for each mapped item. Use a button or link row only when the row performs an action or navigates.

## Show a small table

Material UI Table components compose into normal table sections and cells:

~~~jsx
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
~~~

A table header should describe its column. Keep the layout responsive, especially when cells contain long values.

## Add Data Grid

Install the community Data Grid package as a separate dependency:

~~~sh
npm install @mui/x-data-grid
~~~

Give the grid a parent with a defined height. Each row needs a unique identifier, normally an <code>id</code> field:

~~~jsx
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
~~~

Column definitions describe how a field is displayed. The available features and license terms differ between the Community, Pro, and Premium packages. Check the MUI X documentation before choosing a package for an application.

## Practice questions

1. When is a list an appropriate way to show data?
2. Why might a semantic table be simpler than Data Grid?
3. Which package provides Data Grid?
4. What React prop provides a stable key for a mapped list item?
5. Why does a Data Grid parent need a defined height?
6. What does a Data Grid row need for identification?
7. What does the <code>flex</code> field in a column definition control?
8. Why should package features and license terms be checked before choosing an MUI X plan?

## References

- [List](https://mui.com/material-ui/react-list/)
- [Table](https://mui.com/material-ui/react-table/)
- [MUI X Data Grid quickstart](https://mui.com/x/react-data-grid/quickstart/)
- [Data Grid column definition](https://mui.com/x/react-data-grid/column-definition/)