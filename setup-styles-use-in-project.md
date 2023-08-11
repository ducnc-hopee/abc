# Setup styles use in project

## 1/ Add Noto-sans and Public-sans font

in \_document.tsx file, you need to add font as shown below:

```tsx
<link rel="preconnect" href="https://fonts.googleapis.com" />
 <link rel="preconnect" href="https://fonts.gstatic.com" crossOrigin="anonymous" />
 <link
   ref="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100;200;300;400;500;600;700;800;900&family=Public+Sans:ital,wght@0,300;0,500;0,600;0,700;1,300;1,400;1,500;1,600;1,700&display=swap"
   rel="stylesheet"
 />
```

## 2/ Create global variables for css module

You need to create 'global.css' in styles directory:

Based on this  [`Figma`](https://www.figma.com/file/G2hHKINcVDUIB4r6gknVz7/2\_%E3%82%A4%E3%83%B3%E3%82%BF%E3%83%BC%E3%83%95%E3%82%A7%E3%82%A4%E3%82%B9%E9%96%A2%E9%80%A3-\(230729%E3%81%8B%E3%82%89\)?type=design\&node-id=0-1\&mode=design\&t=SXh3uCIhKybSZmfq-0) file, we will have corresponding variables as shown below:

```css
:root {
  /* colors */
  --color-base-900: '#282323';
  --color-base-800: '#3D3939';
  --color-base-700: '#686260';
  --color-base-500: '#ABA9A5';
  --color-base-300: '#DFDCD9';
  --color-base-200: '#EFEEEE';
  --color-base-100: '#F7F6F6';
  --color-base-0: '#FFFFFF';
  --color-accent: '#00B9C7';
  --color-accent-hover: '#67DAE2';
  --color-blue: '#3B8DD8';
  --color-green: '#6BBA05';
  --color-attention: '#E70C0C';
  --color-attention-hover: '#FFAAAA';

  /* font-weight */
  --fw-bold: 700;
  --fw-700: 700;
  --fw-regular: 400;
  --fw-300: 300;

  /* box-shadows */
  --shadow-l1: '0px 2px 10px 0px #0000000F';
  --shadow-l2: '0px 4px 20px 0px #0000001F';
  --shadow-l3: '0px 4px 20px 0px #0000001F';
  --shadow-l4: '0px 4px 40px 0px #3120203D';
  --shadow-l5: '0px 4px 120px 0px #0000003D';

  /* z-index */
  --z-index-mobileStepper: 1000;
  --z-index-fab: 1050;
  --z-index-speedDial: 1050;
  --z-index-appBar: 1100;
  --z-index-drawer: 1200;
  --z-index-modal: 1300;
  --z-index-snackbar: 1400;
  --z-index-tooltip: 1500;
}

head {
  font-family: 'Helvetica Neue', Helvetica, Arial, 'Hiragino Sans', 'ヒラギノ角ゴシック Pro',
    'Hiragino Kaku Gothic Pro', メイリオ, Meiryo, 'ＭＳ Ｐゴシック', 'MS PGothic', sans-serif;
}
```

## 3/ Create Variable styles

Create a file named 'variables.ts' in the theme directory.

Based on this  [`Figma`](https://www.figma.com/file/G2hHKINcVDUIB4r6gknVz7/2\_%E3%82%A4%E3%83%B3%E3%82%BF%E3%83%BC%E3%83%95%E3%82%A7%E3%82%A4%E3%82%B9%E9%96%A2%E9%80%A3-\(230729%E3%81%8B%E3%82%89\)?type=design\&node-id=0-1\&mode=design\&t=SXh3uCIhKybSZmfq-0) file, we will have corresponding variables as shown below:

```tsx
export const colors = {
  base: {
    900: '#282323',
    800: '#3D3939',
    700: '#686260',
    500: '#ABA9A5',
    300: '#DFDCD9',
    200: '#EFEEEE',
    100: '#F7F6F6',
    0: '#FFFFFF',
  },
  key: {
    accent: '#00B9C7',
    accentHover: '#67DAE2',
  },
  partner: {
    blue: '#3B8DD8',
    green: '#6BBA05',
  },
  utility: {
    attention: '#E70C0C',
    attentionHover: '#FFAAAA',
  },
} as const;

export const fontWeights = {
  w7: 700,
  bold: 700,
  regular: 400,
  w3: 300,
} as const;

export const zIndex = {
  mobileStepper: 1000,
  fab: 1050,
  speedDial: 1050,
  appBar: 1100,
  drawer: 1200,
  modal: 1300,
  snackbar: 1400,
  tooltip: 1500,
} as const;

export const shadows = {
  l1: '0px 2px 10px 0px #0000000F',
  l2: '0px 4px 20px 0px #0000001F',
  l3: '0px 4px 20px 0px #0000001F',
  l4: '0px 4px 40px 0px #3120203D',
  l5: '0px 4px 120px 0px #0000003D',
};
```

## 4/ Config theme for MUI

### 4.1/ Create theme

You need to create a theme for MUI in theme/index.ts with the following code:

```tsx
import { createTheme } from '@mui/material/styles';

const theme = createTheme({});

export default theme;
```

And then, you should pass theme as props into ThemeProvider

```tsx
import {ThemeProvider } from '@mui/material';
import CssBaseline from '@mui/material/CssBaseline';
import theme from '~theme';

function MyApp({ Component, pageProps }) {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <Component {...pageProps} />
    </ThemeProvider>
  );
}

export default MyApp;
```

### 4.2/ Config style for MUI theme

#### 4.2.1/ Create Palette object

you need to create 'palette.ts' file in theme directory with the following code:

```tsx
import { Key } from 'react';
import { colors } from './variables';

declare module '@mui/material/styles' {
  interface Palette {
    [key: string]: Palette['primary'];
  }
  interface PaletteOptions {
    [key: string]: Record<Key, unknown>;
  }
}

declare module '@mui/material/Button' {
  interface ButtonPropsColorOverrides {
    [key: string]: true;
  }
}

const ObjColor = (color: string) => ({
  light: color,
  main: color,
  dark: color,
  darker: color,
});

export const palette = {
  base900: ObjColor(colors.base[900]),
  base800: ObjColor(colors.base[800]),
  base700: ObjColor(colors.base[700]),
  base500: ObjColor(colors.base[500]),
  base300: ObjColor(colors.base[300]),
  base200: ObjColor(colors.base[200]),
  base100: ObjColor(colors.base[100]),
  base0: ObjColor(colors.base[0]),
  accent: ObjColor(colors.key.accent),
  accentHover: ObjColor(colors.key.accentHover),
  blue: ObjColor(colors.partner.blue),
  green: ObjColor(colors.partner.green),
  attention: ObjColor(colors.utility.attention),
  attentionHover: ObjColor(colors.utility.attentionHover),
};
```

#### 4.2.2/ Config typography

you need to create 'typography.ts' file in theme directory with the following code:

```tsx
import { TypographyOptions } from '@mui/material/styles/createTypography';
// eslint-disable-next-line camelcase
import { fontWeights } from './variables';

declare module '@mui/material/styles' {
  interface TypographyVariants {
    fontFamily: string;
    // Heading
    headXL700: React.CSSProperties;
    headL700: React.CSSProperties;
    headM700: React.CSSProperties;
    headS700: React.CSSProperties;
    // sp/Heading
    spHeadXL700: React.CSSProperties;
    spHeadL700: React.CSSProperties;
    spHeadS700: React.CSSProperties;
    // Display
    displayLBold: React.CSSProperties;
    displayMBold: React.CSSProperties;
    displaySBold: React.CSSProperties;
    displaySRegular: React.CSSProperties;
    // sp/Display
    spDisplaySRegular: React.CSSProperties;
    // Body
    bodyXL700: React.CSSProperties;
    bodyL700: React.CSSProperties;
    bodyM700: React.CSSProperties;
    bodyM300: React.CSSProperties;
    bodyS700: React.CSSProperties;
    bodyS300: React.CSSProperties;
    // sp/Body
    spBodyM700: React.CSSProperties;
    spBodyM300: React.CSSProperties;
    spBodyS300: React.CSSProperties;
    // Label
    labelL700: React.CSSProperties;
    labelL300: React.CSSProperties;
    labelM700: React.CSSProperties;
    labelM300: React.CSSProperties;
    labelS700: React.CSSProperties;
    labelS300: React.CSSProperties;
    caption: React.CSSProperties;
    // sp/Label
    spLabelL700: React.CSSProperties;
    spLabelM300: React.CSSProperties;
    spLabelS700: React.CSSProperties;
    spLabelS300: React.CSSProperties;
    spCaption: React.CSSProperties;
  }

  // Update the Typography's variant prop options
  interface TypographyVariantsOptions {
    fontFamily: string;
    // Heading
    headXL700: React.CSSProperties;
    headL700: React.CSSProperties;
    headM700: React.CSSProperties;
    headS700: React.CSSProperties;
    // sp/Heading
    spHeadXL700: React.CSSProperties;
    spHeadL700: React.CSSProperties;
    spHeadS700: React.CSSProperties;
    // Display
    displayLBold: React.CSSProperties;
    displayMBold: React.CSSProperties;
    displaySBold: React.CSSProperties;
    displaySRegular: React.CSSProperties;
    // sp/Display
    spDisplaySRegular: React.CSSProperties;
    // Body
    bodyXL700: React.CSSProperties;
    bodyL700: React.CSSProperties;
    bodyM700: React.CSSProperties;
    bodyM300: React.CSSProperties;
    bodyS700: React.CSSProperties;
    bodyS300: React.CSSProperties;
    // sp/Body
    spBodyM700: React.CSSProperties;
    spBodyM300: React.CSSProperties;
    spBodyS300: React.CSSProperties;
    // Label
    labelL700: React.CSSProperties;
    labelL300: React.CSSProperties;
    labelM700: React.CSSProperties;
    labelM300: React.CSSProperties;
    labelS700: React.CSSProperties;
    labelS300: React.CSSProperties;
    caption: React.CSSProperties;
    // sp/Label
    spLabelL700: React.CSSProperties;
    spLabelM300: React.CSSProperties;
    spLabelS700: React.CSSProperties;
    spLabelS300: React.CSSProperties;
    spCaption: React.CSSProperties;
  }
}

declare module '@mui/material/Typography' {
  interface TypographyPropsVariantOverrides {
    fontFamily: true;
    // Heading
    headXL700: true;
    headL700: true;
    headM700: true;
    headS700: true;
    // sp/Heading
    spHeadXL700: true;
    spHeadL700: true;
    spHeadS700: true;
    // Display
    displayLBold: true;
    displayMBold: true;
    displaySBold: true;
    displaySRegular: true;
    // sp/Display
    spDisplaySRegular: true;
    // Body
    bodyXL700: true;
    bodyL700: true;
    bodyM700: true;
    bodyM300: true;
    bodyS700: true;
    bodyS300: true;
    // sp/Body
    spBodyM700: true;
    spBodyM300: true;
    spBodyS300: true;
    // Label
    labelL700: true;
    labelL300: true;
    labelM700: true;
    labelM300: true;
    labelS700: true;
    labelS300: true;
    caption: true;
    // sp/Label
    spLabelL700: true;
    spLabelM300: true;
    spLabelS700: true;
    spLabelS300: true;
    spCaption: true;
  }
}

export const typography: TypographyOptions = {
  fontFamily: [
    'Helvetica Neue',
    'Helvetica',
    'Arial',
    'Hiragino Sans',
    'ヒラギノ角ゴシック Pro',
    'Hiragino Kaku Gothic Pro',
    'メイリオ',
    'Meiryo',
    'ＭＳ Ｐゴシック',
    'MS PGothic',
    'sans - serif',
  ].join(','),
  // Heading
  headXL700: {
    fontSize: '24px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  headL700: {
    fontSize: '22px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  headM700: {
    fontSize: '18px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  headS700: {
    fontSize: '16px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  // sp/Heading
  spHeadXL700: {
    fontSize: '24px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  spHeadL700: {
    fontSize: '22px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  spHeadS700: {
    fontSize: '16px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  // Display
  displayLBold: {
    fontSize: '24px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.bold,
  },
  displayMBold: {
    fontSize: '16px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.bold,
  },
  displaySBold: {
    fontSize: '12px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.bold,
  },
  displaySRegular: {
    fontSize: '12px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.regular,
  },
  // sp/Display
  spDisplaySRegular: {
    fontSize: '15px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.regular,
  },
  // Body
  bodyXL700: {
    fontSize: '24px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  bodyL700: {
    fontSize: '16px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  bodyM700: {
    fontSize: '14px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  bodyM300: {
    fontSize: '14px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  bodyS700: {
    fontSize: '12px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  bodyS300: {
    fontSize: '12px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  // sp/Body
  spBodyM700: {
    fontSize: '13px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  spBodyM300: {
    fontSize: '13px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  spBodyS300: {
    fontSize: '12px',
    lineHeight: '160%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  // Label
  labelL700: {
    fontSize: '14px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  labelL300: {
    fontSize: '14px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  labelM700: {
    fontSize: '13px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  labelM300: {
    fontSize: '13px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  labelS700: {
    fontSize: '12px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  labelS300: {
    fontSize: '12px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  caption: {
    fontSize: '11px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  // sp/Label
  spLabelL700: {
    fontSize: '17px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  spLabelM300: {
    fontSize: '16px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  spLabelS700: {
    fontSize: '15px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w7,
  },
  spLabelS300: {
    fontSize: '15px',
    lineHeight: '100%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
  spCaption: {
    fontSize: '12px',
    lineHeight: '140%',
    letterSpacing: '0.01em',
    fontWeight: fontWeights.w3,
  },
} as const;

```

#### 4.3.3/ Add palette and typography to MUI theme

```tsx
import { createTheme } from '@mui/material/styles';
import { palette } from './palette';
import { typography } from './typography';

const theme = createTheme({
  palette,
  typography,
});

export default theme;

```
