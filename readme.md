# Next.js + Typescript + Awesome typescript loader

<p>
  <a href="https://www.npmjs.com/package/next-awesome-typescript">
    <img alt="npm" src="https://img.shields.io/npm/v/next-awesome-typescript.svg?style=flat-square" />
  </a>
</p>

Use [Typescript](https://www.typescriptlang.org/) with [Next.js](https://github.com/zeit/next.js) with [Awesome typescipt loader](https://github.com/s-panferov/awesome-typescript-loader)

## Installation

```
npm install --save-dev next-awesome-typescript typescript
```

or

```
yarn add --dev next-awesome-typescript typescript
```

## Usage

Create a `next.config.js` in your project

```js
// next.config.js
const withAwesomeTypescript = require("next-awesome-typescript");
module.exports = withAwesomeTypescript();
```

Minimal `tsconfig.json` is necessary. The reason for it is that babel will be applied after typescript, and will take care of modules, jsx and stuff.

```json
{
  "compileOnSave": false,
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "jsx": "preserve",
    "moduleResolution": "node",
    "sourceMap": true
  }
}
```

You can pass options to `awesome-typescript-loader` as a first argument

```js
// next.config.js
const withAwesomeTypescript = require("next-awesome-typescript");

const awesomeTypescriptOptions = {
  useCheckerPlugin: true,
  loaderOptions: {
    transpileOnly: false,
  },
};

module.exports = withAwesomeTypescript(awesomeTypescriptOptions);
```

Optionally you can add your custom Next.js configuration as a parameter

```js
// next.config.js
const withAwesomeTypescript = require("next-awesome-typescript");
module.exports = withAwesomeTypescript({
  webpack(config, options) {
    // you can optionally add custom Next.js configuration here.
    return config
  },
  awesomeTypescriptOptions: {
    useCheckerPlugin: true,
    loaderOptions: {
      transpileOnly: false,
  }}
});
```

Probably You are not only going to use typescript plugin. In a multi plugin scenario.(In this example with next-css)

```js
// next.config.js
const awesomeTypescriptOptions: {
  useCheckerPlugin: true,
  loaderOptions: {
    transpileOnly: false,
}}

module.exports = withAwesomeTypescript(withCSS({
  cssModules: true,
  cssLoaderOptions: {
    importLoaders: 1,
  },
  awesomeTypescriptOptions
}));
```
