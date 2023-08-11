# Config Eslint

## 1/ Create eslint

In this project, you need to install some packages of ESLint using the following command:

```bash
yarn add —dev @typescript-eslint/eslint-plugin eslint-config-airbnb eslint-config-prettier eslint-import-resolver-typescript eslint-plugin-prettier eslint-plugin-unused-imports lint-staged stylelint stylelint-config-standardbas
```

After that, you need to create 2 files .eslintrc.json and .eslintignore with the following:

```json
// .eslintrc.json
{
  "env": {
    "browser": true,
    "es6": true
  },
  "extends": [
    "next/core-web-vitals",
    "plugin:react/recommended",
    "airbnb",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "globals": {
    "Atomics": "readonly",
    "SharedArrayBuffer": "readonly"
  },
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 2018,
    "sourceType": "module",
    "project": "./tsconfig.json"
  },
  "plugins": ["react", "react-hooks", "@typescript-eslint", "unused-imports"],
  "rules": {
    "quotes": ["warn", "single"],
    "prefer-promise-reject-errors": ["off"],
    "react/jsx-filename-extension": ["off"],
    "react/require-default-props": "off",
    "react/no-unused-prop-types": "off",
    "react/default-props-match-prop-types": "off",
    "react/function-component-definition": "off",
    "react/no-unstable-nested-components": "warn",
    "react/jsx-no-useless-fragment": "warn",
    "react/prop-types": ["off"],
    "no-return-assign": ["off"],
    "import/no-unresolved": "off",
    "react/destructuring-assignment": "off",
    "no-use-before-define": "off",
    "no-param-reassign": [
      "error",
      {
        "props": false
      }
    ],
    "no-shadow": "off",
    "@typescript-eslint/no-use-before-define": [
      "error",
      {
        "variables": false
      }
    ],
    "import/no-extraneous-dependencies": [
      "error",
      { "devDependencies": false, "optionalDependencies": false, "peerDependencies": false }
    ],
    "@typescript-eslint/no-misused-promises": "off",
    "@typescript-eslint/no-floating-promises": "warn",
    "@typescript-eslint/no-shadow": ["error"],
    "@typescript-eslint/ban-types": "off",
    "react/jsx-one-expression-per-line": "off",
    "react/jsx-props-no-spreading": "off",
    "import/prefer-default-export": "off",
    "@typescript-eslint/no-unused-vars": "off",
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "js": "never",
        "jsx": "never",
        "ts": "never",
        "tsx": "never",
        "mjs": "never",
        "": "never"
      }
    ],
    "react/react-in-jsx-scope": "off",
    "@typescript-eslint/ban-ts-comment": "off",
    "@typescript-eslint/array-type": [
      "error",
      {
        "default": "array"
      }
    ],
    "jsx-a11y/anchor-is-valid": [
      "error",
      {
        "components": ["Link"],
        "specialLink": ["to"],
        "aspects": ["noHref"]
      }
    ],
    "require-await": "error",
    "no-restricted-syntax": [
      "error",
      {
        "selector": "TSEnumDeclaration:not([const=true])",
        "message": "Don't declare non-const enums"
      }
    ],
    "react-hooks/rules-of-hooks": "warn",
    "react-hooks/exhaustive-deps": "warn",
    "unused-imports/no-unused-imports": "warn",
    "unused-imports/no-unused-vars": [
      "warn",
      { "vars": "all", "varsIgnorePattern": "^_", "args": "after-used", "argsIgnorePattern": "^_" }
    ],
    "import/no-cycle": "warn",
    "import/no-named-as-default": "warn"
  },
  "overrides": [
    {
      "files": ["src/**/*.tsx"],
      "excludedFiles": ["src/**/*.test.tsx"],
      "rules": {
        "max-lines": [
          "warn",
          {
            "max": 500
          }
        ]
      }
    }
  ]
}

```

```ignore
// .eslintignore
# dependencies
/node_modules
/.pnp
.pnp.js
next.config.js
shipitfile.js

# testing
/coverage

# next.js
/.next/
/out/

# production
/build

# misc
.DS_Store
*.pem

# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# local env files
.env.local

# vercel
.vercel
```

### 2/ Set up testing scripts:

```json
"scripts": {
    "lint": "next lint",
},
```
