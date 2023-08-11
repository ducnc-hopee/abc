# Material-UI (MUI)

## 1/ Install MUI

To install Material-UI, use the following command:

```bash
yarn add @mui/material @emotion/react @emotion/styled
```

## 2/ **Wrap your App with MuiThemeProvider**:

In your `_app.tsx` file (located in the `pages` directory), wrap your app with the `MuiThemeProvider` component and provide the customized theme:

```tsx
import {ThemeProvider, useTheme } from '@mui/material';
import CssBaseline from '@mui/material/CssBaseline';

function MyApp({ Component, pageProps }) {
  const theme = useTheme();
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <Component {...pageProps} />
    </ThemeProvider>
  );
}

export default MyApp;
```
