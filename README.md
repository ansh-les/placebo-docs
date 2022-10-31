<!-- markdownlint-disable-next-line -->
<!-- <p align="center">
  <a href="https://mui.com/" rel="noopener" target="_blank"><img width="150" src="https://mui.com/static/logo.svg" alt="MUI logo"></a>
</p> -->

<h1 align="center">Placebo UI</h1>

**Placebo UI** contains foundational React UI component libraries for shipping new features faster.
 

<div align="center">
<!-- 
**[Stable channel v5](https://mui.com/)** -->

[![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white)](https://www.google.com/)
[![yarn latest package](https://badgen.net/badge/yarn@latest/0.1.14/blue?icon=label)](https://www.google.com/)
 
</div>

## Installation

### Placebo UI

Placebo UI is available as an [yarn package](https://www.google.com/).
Followed by necessary necessary dependencies like 
- react-jss available as an [yarn package](https://cssinjs.org/react-jss/?v=v10.9.1-alpha.2)
- iconoir-react available as an [yarn package](https://iconoir.com/)

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