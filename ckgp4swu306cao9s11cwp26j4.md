## An easy React 17 + TypeScript + Tailwind CSS + NextJS setup

NextJS is becoming a de facto framework for modern web development. In this article we will build a starter repo that you can use for every new project.

## Tech Stack:

*   [React](https://reactjs.org/)
*   [TypeScript](https://www.typescriptlang.org/)
*   [Tailwind CSS](https://tailwindcss.com/)
*   [Next JS](https://nextjs.org/)

## Creating a new project

As with any new project, we'll create a new directory for our starter repo and initialize it with npm/yarn:

```bash
mkdir next-ts-starter
cd next-ts-starter
yarn init
```

_Hit enter on everything if you don't want to configure your npm package yet._

This will create a `package.json` file for you. That's all we need to start adding the other packages.

## Setting up TypeScript

We'll add the TypeScript packages first, so later we can immediately add the typings. First, let's add the TypeScript package as a dev dependency:

```bash
yarn add --dev typescript
```

Then, we will need to create a new file in the root directory called `tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": false,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "sourceMap": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve"
  },
  "include": [
    "next-env.d.ts",
    "**/*.ts",
    "**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

Now let's start adding our packages.

## Installing React

Installing react is straightforward. We'll only need to add the following npm packages:

```bash
yarn add react react-dom
```

And the TypeScript support packages:

```bash
yarn add --dev @types/node @types/react
```

## Setting up Next JS

First, we'll need to add the Next JS package:

```bash
yarn add next
```

Now let's go back to `packages.json` and add the Next JS scripts:
```json
...
"scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
},
...
```

Then we'll need to create a `next-env.d.ts` file for the types:
```typescript
/// <reference types="next" />
/// <reference types="next/types/global" />
```

And optionally, we can create the `next.config.js` file in which we can extend the webpack config, or add our environment variables:
```javascript
module.exports = {
  distDir: 'build',
  publicRuntimeConfig: {
    // add your public runtime environment variables here with NEXT_PUBLIC_*** prefix
  },
  webpack: (config) => {
    // extend your webpack configuration here
    return config;
  },
}
```

Now let's create the initial page and test if it works. Create a new directory called `pages` in the root, and inside create an `index.tsx` file:
```typescript
const IndexPage = () => {
  return (
    <h1>Hello, CodeChem!</h1>
  )
};

export default IndexPage;
```

_**Tip**: as with React 17, you don't need to add "import React from 'react';" in your component files anymore!_

Okay so now let's execute `yarn dev` and head to [http://localhost:3000](http://localhost:3000). You should see the "Hello, CodeChem!" heading. And that means everything works fine and we're ready to move on.

## Setting up Tailwind CSS

First, we'll need to install the `tailwindcss` package:
```bash
yarn add tailwindcss
```

Optionally, we can create the empty `tailwind.config.js` file in the root directory:
```javascript
module.exports = {
    important: true,
    purge: ['./pages/**/*.tsx'],
    theme: {},
    variants: {},
    plugins: [],
};
```

_**Tip**: to completely utilize the purging functionality, add your new folders in the second line with the **tsx** postfix._

Next, we'll need to install the `postcss-import` package:
```bash
yarn add postcss-import@^12.0.0
```

> At the time of writing this article, `postcss-import` version `13.0.0` is breaking the tailwind implementation, therefore we will explicitly use the `^12.0.0` version.


Then create a new file `postcss.config.js` file:
```javascript
module.exports = {
  plugins: [
    'postcss-import',
    'tailwindcss',
    'autoprefixer',
  ],
};
```

In order to include Tailwind into our app, first we'll need to create a new CSS file in the root directory that includes Tailwind CSS. You can name this as you wish. We'll name it `global.css` for now:
```css
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

Now, in order to include it in our app, we'll need to override Next JS's `_app.tsx` page by creating a new file: `pages/_app.tsx`:
```typescript
import { AppProps } from 'next/app';

import '../global.css';

const App = ({ Component, pageProps }: AppProps) => (
  <Component {...pageProps} />
);

export default App;
```

So to validate that everything works, let's head back to `index.tsx` and add a tailwind class to the `<h1>Hello, CodeChem!</h1>` like so:
```html
<h1 className="text-green-500">Hello, CodeChem!</h1>
```
Execute `yarn dev` and go to [http://localhost:3000](http://localhost:3000). You should see the label with smaller font size than previously and with green text color.

## Bonus

For better code consistency and developer experience, let's install and configure the Prettier and Eslint plugins to work with TypeScript.

### Eslint

First, let's install Eslint and its React plugins:
```bash
yarn add --dev eslint eslint-plugin-react eslint-plugin-react-hooks
```

Then we need to add Eslint's typings:
```bash
yarn add --dev @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

With that in place, let's create the Eslint config file `.eslintrc.js` in the root directory:
```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  extends: [
      'plugin:react/recommended',
      'plugin:@typescript-eslint/recommended',
      'plugin:react-hooks/recommended',
  ],
  parserOptions: {
      ecmaVersion: 2020,
      sourceType: 'module',
      ecmaFeatures: {
          jsx: true,
      },
  },
  rules: {

  },
  settings: {
      react: {
          version: 'detect',
      },
  },
};
```

And that's it! If you're using Visual Studio Code and Eslint doesn't automatically start, a reload won't hurt.

Also, since you don't need to import React since React 17, Eslint might still suggest you do. In order to fix that, head to `.eslintrc.js` and add the following line in the `rules` section:
```json
'react/react-in-jsx-scope': 'off',
```


### Prettier

To top it off, we'll add Prettier into the mix! Let's start by installing the Prettier package and the Eslint plugin:

```bash
yarn add --dev prettier eslint-config-prettier eslint-plugin-prettier
```

Now let's create a `.prettierrc.js` file in the root directory:
```javascript
module.exports =  {
    semi: true,
    trailingComma: 'all',
    singleQuote: true,
    printWidth: 120,
    tabWidth: 4,
    quoteProps: 'preserve'
 };
```

And to configure Eslint to work with Prettier, let's head back to `.eslintrc.js` to add the Prettier extensions in the `extends` array:
```javascript
'prettier/@typescript-eslint',
'plugin:prettier/recommended',
```

Your final `.eslintrc.js` should look like this:
```javascript
module.exports = {
    parser: '@typescript-eslint/parser',
    extends: [
        'plugin:react/recommended',
        'plugin:@typescript-eslint/recommended',
        'plugin:react-hooks/recommended',
        'prettier/@typescript-eslint',
        'plugin:prettier/recommended',
    ],
    parserOptions: {
        ecmaVersion: 2020,
        sourceType: 'module',
        ecmaFeatures: {
            jsx: true,
        },
    },
    rules: {},
    settings: {
        react: {
            version: 'detect',
        },
    },
};
```

And that's it! You can push this in a separate GitHub project and use it as a starter for your new projects.