# Next.js + Sass + CSS Modules + Storybook

## Setup Process

1. Initialize Next.js Project and Storybook

```bash
npx create-next-app@latest
npx storybook@latest init
```

2. ESlint, Prettier Configuration
- Refer https://github.com/hikarucraft/nextjs-template-tailwind-storybook

3. Additional npm

```bash
npm install -D ress sass classnames
```

4. Stylelint Installation and configuration

```bash
npm install -D stylelint stylelint-scss stylelint-config-recess-order stylelint-config-recommended-scss
touch .stylelintrc.json
```

- `.stylelintrc.json`

```json
{
  "plugins": ["stylelint-scss"],
  "extends": ["stylelint-config-recess-order", "stylelint-config-recommended-scss"], 
  "rules": {
    // recommended rules
    "at-rule-no-unknown": null,
    "scss/at-rule-no-unknown": true,
  }
}
```

- package.json

```json
{
    //...
  "scripts": {
    //...
    "lint:style": "stylelint './**/*.{css,scss}'",
    "lint:style:fix": "stylelint --fix './**/*.{css,scss}'",
    //...
  }
}
```

- `.vscode/settings.json`

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.stylelint": true //<- add
  },
  "stylelint.validate": ["css", "scss"], //<- add
}
```
- `.vscode/extentions.json`

```json
{
  "recommendations":[
    //...
    "stylelint.vscode-stylelint"
    //...
  ]
}
```
5. Happy CSS Modules

```bash
npm install -D happy-css-modules
```

- `settings.json`

```json
{
  //...
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.patterns": {
    "*.module.css": "*.module.css.d.ts, *.module.css.d.ts.map"
  }
  //...
}
```

- `package.json`

```json
{
  "scripts": {
    //...
    "style:gen:watch": "hcm 'src/**/*.module.{css,scss,less}' --watch",
    "style:gen": "hcm 'src/**/*.module.{css,scss,less}'"
    //...
  }
}
```

- `.gitignore`

```
#...
*.module.css.d.ts
*.module.css.d.ts.map
#...
```

6. Sass with Storybook

```bash
npm install -D @storybook/nextjs
```

- `.storybook/main.js`

```js
export default {
  // ...
  framework: {
    // name: '@storybook/react-webpack5', // Remove this
    name: '@storybook/nextjs', // Add this
    options: {},
  },
};
```

## Refs.
- https://zenn.dev/yumemi_inc/articles/make-css-modules-happy
- https://yumegori.com/vscode-nextjs-typescript-eslint-prettier
- https://storybook.js.org/recipes/sass#sass
- https://storybook.js.org/recipes/next#next



This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
