# Config eslint and prettier

## Install eslint and prettier

```bash	
npm init @eslint/config
```

```bash
npm install --save-dev prettier eslint-plugin-prettier eslint-config-prettier
```

## Create .eslint.config.js

```javascript
import globals from 'globals';
import pluginJs from '@eslint/js';
import tseslint from 'typescript-eslint';
import prettier from 'eslint-config-prettier';// add after install prettier
import prettierPlugin from 'eslint-plugin-prettier'; // add after install prettier

export default [
  { files: ['**/*.{js,mjs,cjs,ts}'] },
  { languageOptions: { globals: globals.browser } },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  prettier,// add after install prettier
  {
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      'prettier/prettier': 'error',
    },
  },
];
```

## eslint ignore in .eslint.config.js

```javascript
export default [
  { files: ['**/*.{js,mjs,cjs,ts}'] },
  { languageOptions: { globals: globals.browser } },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  prettier,
  {
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      'prettier/prettier': 'error',
    },
  },
  {
    ignorePatterns: ['node_modules/', 'dist/', 'build/'],
  },
];
```

## Create .prettierrc

```json
{
  "$schema": "https://json.schemastore.org/prettierrc",
  "semi": true,
  "tabWidth": 2,
  "singleQuote": true,
  "printWidth": 100,
  "arrowParens": "avoid",
  "trailingComma": "all"
}
```

## Create .vscode/settings.json

```json
{
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": "explicit",
      "source.organizeImports": "explicit"
    },
    "eslint.validate": [
      "javascript",
      "javascriptreact",
      "typescript",
      "typescriptreact",
      "vue"
    ],
    "prettier.requireConfig": true,
    "editor.tabSize": 2,
    "editor.detectIndentation": false,
    "[javascript]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[typescript]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[vue]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "prettier.enable": true,
    "prettier.singleQuote": true,
    "prettier.semi": true,
    "prettier.trailingComma": "es5",
    "prettier.printWidth": 100,
    "prettier.tabWidth": 2,
    "prettier.useTabs": false
  }
```