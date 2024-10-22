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