# 99. Complete questions and answers

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: All code samples](./98-all-code-samples.md) | [Notes index](../README.md) | End of notes |

This appendix gathers the review questions from each chapter and provides a direct answer for every one.

## Chapter 1: Getting started with Material UI

Source: [Open chapter](./01-getting-started-with-material-ui.md)

### Question 1

What does Material UI provide to a React application?

**Answer:** Material UI supplies ready-made React interface components and customization tools.

### Question 2

Which package contains the standard Material UI components?

**Answer:** <code>@mui/material</code> contains the standard Material UI component library.

### Question 3

Why must React and React DOM already be installed?

**Answer:** React and React DOM are peer dependencies, so the React application must provide them.

### Question 4

Which styling engine is used by the default installation?

**Answer:** Emotion is the default styling engine.

### Question 5

Are MUI X components included in the Material UI package?

**Answer:** No. MUI X is distributed in separate packages such as <code>@mui/x-data-grid</code>.

### Question 6

What does the Button <code>variant</code> prop change in the example?

**Answer:** The <code>variant</code> prop selects a documented appearance, such as contained, outlined, or text.

### Question 7

What does <code>CssBaseline</code> provide?

**Answer:** <code>CssBaseline</code> applies base styles that make common page defaults more consistent.

### Question 8

Why does a page need a responsive viewport meta tag?

**Answer:** It tells mobile browsers to use the device width so responsive layouts do not render as a zoomed desktop page.

## Chapter 2: Components, props, and composition

Source: [Open chapter](./02-components-props-and-composition.md)

### Question 1

What is the supported way to configure a Material UI component?

**Answer:** Props are the documented way to configure a component appearance, content, state, and behavior.

### Question 2

Why should you check the component API page before using a prop?

**Answer:** The API page documents accepted values, defaults, semantics, and component behavior.

### Question 3

What does the <code>children</code> prop represent?

**Answer:** <code>children</code> is the content placed between a component opening and closing tag.

### Question 4

What does component composition mean?

**Answer:** Composition means building a larger interface by combining smaller components with clear roles.

### Question 5

When is an anchor a better semantic choice than a button?

**Answer:** An anchor link is appropriate when activating the control navigates to another destination.

### Question 6

What does the <code>component</code> prop let you change?

**Answer:** The <code>component</code> prop changes the rendered root element while keeping the component behavior and styling.

### Question 7

Why should a reusable wrapper forward useful component props?

**Answer:** A wrapper should expose required customization, such as event handlers, accessible labels, and supported styling props.

### Question 8

Why should application code avoid depending on generated internal class names?

**Answer:** Generated hash-prefixed classes can change between builds and are not stable public selectors.

## Chapter 3: Typography, surfaces, and layout

Source: [Open chapter](./03-typography-surfaces-and-layout.md)

### Question 1

What does the Typography <code>variant</code> prop select?

**Answer:** <code>variant</code> selects a predefined text appearance from the theme.

### Question 2

Which prop can choose the HTML heading element?

**Answer:** <code>component</code> can select the semantic HTML heading element.

### Question 3

What does Container help control?

**Answer:** <code>Container</code> centers content and constrains its maximum width.

### Question 4

Which layout component is useful for one-dimensional spacing?

**Answer:** <code>Stack</code> arranges children in one direction with consistent spacing.

### Question 5

What is the default Material UI theme spacing unit?

**Answer:** The default theme spacing unit is 8 pixels.

### Question 6

When is Card a useful choice?

**Answer:** <code>Card</code> is useful for a related content item with its own content and action structure.

### Question 7

Why should heading levels follow a meaningful order?

**Answer:** Logical heading order exposes the page outline to assistive technology and makes sections easier to navigate.

### Question 8

Does a Divider provide a semantic section heading?

**Answer:** No. A Divider is a visual separator, not a semantic heading.

## Chapter 4: Buttons, links, and icons

Source: [Open chapter](./04-buttons-links-and-icons.md)

### Question 1

What are the three common Button variants?

**Answer:** The common Button variants are text, outlined, and contained.

### Question 2

Which variant is usually suitable for the primary action?

**Answer:** A contained button is usually suitable for the main action on a view.

### Question 3

When does Button render as an anchor?

**Answer:** Button renders as an anchor when it receives an <code>href</code>.

### Question 4

What should a navigation action use, a link or a button?

**Answer:** Use a link for navigation and a button for an action.

### Question 5

Why does an icon-only control need an accessible name?

**Answer:** An icon-only control has no visible text, so it needs another accessible name.

### Question 6

Is a tooltip a replacement for the icon button label?

**Answer:** No. A tooltip can help sighted users, but the control still needs an accessible name.

### Question 7

Which prop places an icon before Button content?

**Answer:** <code>startIcon</code> places an icon before the Button text.

### Question 8

When is ButtonGroup useful?

**Answer:** <code>ButtonGroup</code> is useful for a small set of related actions or choices.

## Chapter 5: Forms and input controls

Source: [Open chapter](./05-forms-and-input-controls.md)

### Question 1

Which component combines a label and input for a common text field?

**Answer:** <code>TextField</code> combines a label, input, and helper text for a common text entry control.

### Question 2

Why should an input have a visible label?

**Answer:** A visible label tells people what information belongs in the field and gives assistive technology its name.

### Question 3

What makes a React input controlled?

**Answer:** A controlled input reads its value from React state and uses a callback to update that state.

### Question 4

Should one input switch between <code>value</code> and <code>defaultValue</code>?

**Answer:** No. Choose either a controlled value or an uncontrolled initial value and keep that mode for the field lifetime.

### Question 5

What connects the visible Select label to the control?

**Answer:** <code>labelId</code> connects the visible <code>InputLabel</code> to the Select control.

### Question 6

Which input suits multiple independent choices?

**Answer:** A Checkbox suits independent on or off choices.

### Question 7

Which input suits one choice from a group?

**Answer:** A RadioGroup suits a single choice from a set of options.

### Question 8

Why must the server validate form data even when the browser already checked it?

**Answer:** Client-side checks can be bypassed, so the server must validate values before trusting or storing them.

## Chapter 6: Dialogs, menus, and feedback

Source: [Open chapter](./06-dialogs-menus-and-feedback.md)

### Question 1

When is Snackbar useful?

**Answer:** Snackbar is useful for brief feedback that should not move the page content.

### Question 2

Why should important information not appear only in a temporary Snackbar?

**Answer:** A temporary message can disappear before someone reads it, so essential information must remain available elsewhere.

### Question 3

What does Alert severity communicate?

**Answer:** Alert severity communicates whether feedback is success, information, warning, or error.

### Question 4

Which component can request confirmation before an action?

**Answer:** <code>Dialog</code> can present information and ask a person to confirm a decision.

### Question 5

What should a confirmation dialog explain?

**Answer:** It should describe the consequence of the decision and make each action clear.

### Question 6

What does Menu use to decide where it opens?

**Answer:** <code>anchorEl</code> identifies the element that positions the Menu.

### Question 7

Why should a menu-opening button expose its expanded state?

**Answer:** Expanded state communicates whether a control has opened a menu, which helps assistive technology and keyboard users.

### Question 8

Where should focus normally return when a dialog or menu closes?

**Answer:** Focus should normally return to the control that opened the surface.

## Chapter 7: Lists, tables, and Data Grid

Source: [Open chapter](./07-lists-tables-and-data-grid.md)

### Question 1

When is a list an appropriate way to show data?

**Answer:** A list suits related items where each item can have a label, supporting text, or an action.

### Question 2

Why might a semantic table be simpler than Data Grid?

**Answer:** A semantic table is simpler when the set is small and does not need interactive sorting, selection, or pagination.

### Question 3

Which package provides Data Grid?

**Answer:** <code>@mui/x-data-grid</code> provides Data Grid.

### Question 4

What React prop provides a stable key for a mapped list item?

**Answer:** React uses the <code>key</code> prop to identify a mapped child between renders.

### Question 5

Why does a Data Grid parent need a defined height?

**Answer:** A defined height gives the virtualized grid a viewport in which to render and scroll its rows.

### Question 6

What does a Data Grid row need for identification?

**Answer:** A row needs a unique identifier, normally supplied through its <code>id</code> field.

### Question 7

What does the <code>flex</code> field in a column definition control?

**Answer:** Column <code>flex</code> lets the column expand in proportion to other flexible columns.

### Question 8

Why should package features and license terms be checked before choosing an MUI X plan?

**Answer:** Available capabilities and package terms differ between the Community, Pro, and Premium plans.

## Chapter 8: Navigation and application shells

Source: [Open chapter](./08-navigation-and-application-shells.md)

### Question 1

What do AppBar and Toolbar provide?

**Answer:** AppBar and Toolbar provide a top-level bar and a layout for its contents.

### Question 2

Which Drawer variant typically fits a menu opened temporarily on mobile?

**Answer:** A temporary Drawer is commonly used for a menu opened on a small screen.

### Question 3

How can a person close a temporary Drawer without choosing a link?

**Answer:** Escape or backdrop interaction can close a temporary Drawer.

### Question 4

When are Tabs appropriate?

**Answer:** Tabs suit related local views within one section of an application.

### Question 5

When should page destinations use links instead of Tabs?

**Answer:** Use links when the controls navigate to separate pages rather than changing the current local view.

### Question 6

What do breadcrumbs communicate?

**Answer:** Breadcrumbs communicate the current page position within a hierarchy.

### Question 7

Why should navigation have an accessible label?

**Answer:** An accessible label helps people distinguish one navigation region from another.

### Question 8

What layout issue can a fixed AppBar cause?

**Answer:** A fixed bar leaves normal document flow, so content can begin underneath it unless the layout adds space.

## Chapter 9: Themes, palettes, and color schemes

Source: [Open chapter](./09-themes-palettes-and-color-schemes.md)

### Question 1

What does a theme store?

**Answer:** A theme stores shared design choices such as palette, typography, spacing, shape, and component defaults.

### Question 2

Which provider makes the theme available to descendant components?

**Answer:** <code>ThemeProvider</code> makes the theme available to descendant components.

### Question 3

What does <code>CssBaseline</code> do?

**Answer:** <code>CssBaseline</code> applies consistent base styles to the document.

### Question 4

Why use palette roles instead of repeating raw colors?

**Answer:** Palette roles give colors a shared meaning and allow the visual system to be changed consistently.

### Question 5

Which palette setting selects light or dark mode?

**Answer:** <code>palette.mode</code> selects light or dark mode.

### Question 6

Does a palette automatically guarantee sufficient text contrast?

**Answer:** No. Check foreground and background contrast for each custom pairing and state.

### Question 7

Why should a theme object avoid being recreated on every render?

**Answer:** A stable theme avoids repeated object creation and unnecessary downstream updates.

### Question 8

When should a global theme override be used instead of a local style?

**Answer:** Use global overrides for rules that should apply broadly and consistently across the application.

## Chapter 10: The sx prop and responsive styles

Source: [Open chapter](./10-sx-prop-and-responsive-styles.md)

### Question 1

What is the <code>sx</code> prop useful for?

**Answer:** <code>sx</code> is useful for a small local style adjustment that can use theme values.

### Question 2

How does a theme-aware color value differ from a raw color literal?

**Answer:** A theme-aware token refers to a shared design role, while a raw literal fixes one local value.

### Question 3

What does the <code>p</code> shorthand use?

**Answer:** The <code>p</code> shorthand uses the theme spacing scale.

### Question 4

How do responsive object values work across breakpoints?

**Answer:** A responsive value applies at its breakpoint and above until a later breakpoint value overrides it.

### Question 5

What are the default breakpoint names?

**Answer:** The default names are <code>xs</code>, <code>sm</code>, <code>md</code>, <code>lg</code>, and <code>xl</code>.

### Question 6

Why should responsive layouts begin with the narrow layout?

**Answer:** Starting narrow keeps the interface usable on small screens before adding roomier layout changes.

### Question 7

When might a reusable styled component be better than a long <code>sx</code> expression?

**Answer:** A reusable styled component is a better fit when a complex or repeated style needs one shared definition.

### Question 8

When is <code>useMediaQuery</code> needed instead of a CSS breakpoint?

**Answer:** Use <code>useMediaQuery</code> when JavaScript behavior, rather than appearance alone, depends on viewport size.

## Chapter 11: The styled API and theme overrides

Source: [Open chapter](./11-styled-api-and-theme-overrides.md)

### Question 1

Which styling tool suits one local adjustment?

**Answer:** <code>sx</code> is appropriate for one local adjustment.

### Question 2

When is <code>styled</code> useful?

**Answer:** <code>styled</code> is useful for a reusable component whose styles may depend on the theme or props.

### Question 3

Where can a reusable styled component read palette and spacing values?

**Answer:** The callback receives the active theme as its <code>theme</code> argument.

### Question 4

What does <code>shouldForwardProp</code> protect against?

**Answer:** <code>shouldForwardProp</code> prevents a styling-only prop from being passed to an HTML element as an invalid attribute.

### Question 5

Where should application-wide Button defaults be configured?

**Answer:** Configure app-wide Button defaults under <code>components.MuiButton.defaultProps</code> in the theme.

### Question 6

What is the purpose of <code>styleOverrides</code>?

**Answer:** <code>styleOverrides</code> changes shared styles for a Material UI component slot.

### Question 7

Why should a generated hash-prefixed class not be targeted?

**Answer:** Generated class hashes are build details that can change and are not stable selectors.

### Question 8

Why can a large global theme override become difficult to maintain?

**Answer:** A large global override is hard to locate, affects many screens, and can contain styling that belongs to a reusable component.

## Chapter 12: Responsive layouts and breakpoints

Source: [Open chapter](./12-responsive-layouts-and-breakpoints.md)

### Question 1

What does a breakpoint represent?

**Answer:** A breakpoint is a viewport threshold at which a responsive style or layout changes.

### Question 2

How many columns does the default Material UI Grid use?

**Answer:** The default Material UI Grid has 12 columns.

### Question 3

Which prop sets a Grid child's width in the current API?

**Answer:** The current Grid API uses the <code>size</code> prop.

### Question 4

How does the example change at the <code>md</code> breakpoint?

**Answer:** At <code>xs</code> each example region spans all columns and stacks; from <code>md</code>, the regions use 4 and 8 columns.

### Question 5

When is CSS Grid more suitable than Material UI Grid?

**Answer:** CSS Grid is better when layout needs explicit rows, named areas, or automatic item placement.

### Question 6

Why can <code>minmax(0, 1fr)</code> help with long content?

**Answer:** <code>minmax(0, 1fr)</code> allows a track to shrink below its content minimum so long content does not force overflow.

### Question 7

When should <code>useMediaQuery</code> be used?

**Answer:** Use <code>useMediaQuery</code> when application logic needs a different behavior at a viewport threshold.

### Question 8

Why should a server-rendered page test responsive initialization?

**Answer:** The server cannot know the real browser viewport, so the first client render can differ and cause a hydration mismatch.

## Chapter 13: Accessibility and keyboard navigation

Source: [Open chapter](./13-accessibility-and-keyboard-navigation.md)

### Question 1

Which element should be used for navigation to another page?

**Answer:** Use an anchor link for navigation to another page.

### Question 2

Why should a heading look and behave like a heading in the HTML structure?

**Answer:** Semantic headings expose the document outline so assistive technologies and people can navigate sections.

### Question 3

What identifies the purpose of a TextField?

**Answer:** A visible label identifies the information expected by a TextField.

### Question 4

What must an icon-only button include?

**Answer:** An icon-only button needs an accessible name, commonly supplied through <code>aria-label</code>.

### Question 5

Does a tooltip replace an accessible button name?

**Answer:** No. A tooltip does not replace the button accessible name.

### Question 6

Why should focus remain visible?

**Answer:** A visible focus indicator shows keyboard users which control will receive the next action.

### Question 7

What should happen to focus when a Dialog closes?

**Answer:** Focus should return to the control that opened the Dialog, unless that control no longer exists.

### Question 8

Why is color alone insufficient to communicate an error?

**Answer:** Color alone can be missed by people with color vision differences and does not provide a spoken explanation.

## Chapter 14: React state and controlled components

Source: [Open chapter](./14-react-state-and-controlled-components.md)

### Question 1

What role does a Material UI component play when React owns the state?

**Answer:** It renders the interface and reports interaction events while React owns the current value and application logic.

### Question 2

What makes a TextField controlled?

**Answer:** A controlled TextField receives its current <code>value</code> from React state and updates it through an event callback.

### Question 3

Which event property contains the new text field value?

**Answer:** <code>event.target.value</code> contains the current text field value.

### Question 4

Which Checkbox event property contains its checked state?

**Answer:** <code>event.target.checked</code> contains the current Checkbox state.

### Question 5

When is controlled state useful?

**Answer:** Controlled state is useful when an application must validate, submit, reset, or share a value.

### Question 6

What is an uncontrolled field's initial value prop?

**Answer:** An uncontrolled field receives its initial value through <code>defaultValue</code> or <code>defaultChecked</code>.

### Question 7

Why should a field not switch between controlled and uncontrolled modes?

**Answer:** Switching modes can desynchronize React and the DOM and may trigger warnings.

### Question 8

Why should derived values usually be calculated instead of stored twice?

**Answer:** Duplicated state can disagree with its source value and create inconsistent UI.

## Chapter 15: Performance and server rendering

Source: [Open chapter](./15-performance-and-server-rendering.md)

### Question 1

Why should performance changes start with measurement?

**Answer:** Measurement identifies the actual bottleneck because load time, interaction delay, and bundle size have different causes.

### Question 2

Why can broad package imports slow development even when production tree-shakes unused code?

**Answer:** Development tools may process many modules through a broad import even though a production bundler later removes unused code.

### Question 3

Which import form is recommended for Material UI icons?

**Answer:** Use a direct default import such as <code>@mui/icons-material/Add</code>.

### Question 4

Why is Data Grid useful for a large dataset?

**Answer:** Data Grid virtualizes rows so the browser does not need to render the full dataset at once.

### Question 5

Which styling engine is used by the default Material UI setup?

**Answer:** Emotion is the default styling engine.

### Question 6

What can happen when server-rendered styles are not collected correctly?

**Answer:** Without server-collected CSS, the page can briefly display without its intended styles before the browser inserts them.

### Question 7

Why should a custom server render use a new Emotion cache for each request?

**Answer:** A fresh cache per request avoids sharing style state between unrelated server responses.

### Question 8

Why must server and browser theme configuration match?

**Answer:** Matching configuration gives the server markup and browser hydration the same theme and styles.

## Chapter 16: Testing and production patterns

Source: [Open chapter](./16-testing-and-production-patterns.md)

### Question 1

What should a component test focus on?

**Answer:** A component test should focus on visible behavior and interactions a person can use.

### Question 2

Why is querying by role and accessible name useful?

**Answer:** Role and accessible-name queries reflect the semantics people and assistive technology use and are less tied to private markup.

### Question 3

What does <code>userEvent</code> help a test simulate?

**Answer:** <code>userEvent</code> helps simulate user actions such as clicking and typing.

### Question 4

Why should tests avoid generated class names?

**Answer:** Generated class names are unstable implementation details that can change without changing the UI behavior.

### Question 5

When should a test provide the application theme?

**Answer:** Provide the application theme when a component relies on its custom tokens or configuration.

### Question 6

What interaction should be checked by keyboard?

**Answer:** Test that an interactive control can be reached and operated with a keyboard.

### Question 7

What should be verified for a server-rendered page?

**Answer:** Check that the initial HTML includes the expected styles and that hydration completes without a style flash or mismatch.

### Question 8

Why should the production build be checked at realistic viewport sizes?

**Answer:** Realistic viewport sizes reveal overflow, wrapping, and layout problems hidden by a single desktop width.
