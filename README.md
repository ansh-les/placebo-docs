<!-- markdownlint-disable-next-line -->
<!-- <p align="center">
  <a href="https://mui.com/" rel="noopener" target="_blank"><img width="150" src="https://mui.com/static/logo.svg" alt="MUI logo"></a>
</p> -->

# Placebo

![This is an image](/Assets/Cover.png)

Our design system helps us work together to build a great experience for all.

## Colours

### Primary

`#EDF0FE` `#DAE0FD` `#B5C2FB` `#90A3FA` `#6B85F8` `#4666F6` `#3852C5` `#2A3D94` `#1C2962` `#0E1431`
## Installation

Placebo UI is available as an [yarn package](https://www.google.com/).
Followed by necessary necessary dependencies like

```sh
yarn add @suraasa/placebo-ui react-jss iconoir-react
```
This package depends on external libraries. If your project is using Typescript then you will need to install their types externally.

```sh
yarn add -D @types/react-modal
```

## Usage
In order to get on with placebo the application must be wrapped with `ThemeProvider` which can be imported from react-jss.
And import `ThemeProvider` from the package react-jss. 
```jsx
import { ThemeProvider } from "react-jss"
```
With this we need to pass `theme` object (which can be imported from Placebo UI)  to `ThemeProvider` in order to set up a default theme in the application.
```jsx
import { theme } from "@suraasa/placebo-ui"
```
`CSSBaseline` is used in order to reset css ie remove default html styling
```jsx
import { CssBaseline } from "@suraasa/placebo-ui"
```
Now wrap `ThemeProvider` around application and pass theme object.
```jsx
import React from "react"
import { ThemeProvider } from "react-jss"
import { CssBaseline, theme } from "@suraasa/placebo-ui"

function App() {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <HomePage />
    </ThemeProvider>
  )
}

export default App
```

This gives access to create own css classes based on theme for the application by importing `createUseStyles`
```jsx
import React from "react"

import { createUseStyles } from "react-jss"

const useStyles = createUseStyles(theme => ({
  container: {
    margin: theme.spacing(1),
  },
}))
const HomePage = () => {
  const classes = useStyles()
  return (
    <div className={classes.container}>
      <h1>Hello World!</h1>
    </div>
  )
}

export default HomePage
```
By using `createUseStyles` we get access to the theme object passed through `ThemeProvider`.The `theme` provides us with spacing property that by default has the value of `8px` and passing the value of 1 gives margin of `8px`.


## Scripts
```sh
yarn storybook
```
Starts the development server on http://localhost:6006

```sh
yarn create-component <name>
```

Creates a new component with the following files:
 
- `index.ts`
- `Name.tsx`
- `Name.stories.tsx`
- `Name.test.tsx`


```sh
yarn test
```
Run predefined test.


```sh
yarn lint:fix
```

Runs `eslint --fix` on the entire project. Fixes all autofixable issues. Also comes in handy to find issues after a change that affects other files.