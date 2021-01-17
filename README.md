# Webpack 5 fundamentals

# Changelog

## [0.1] - 2021-01-17

> Initialisation of webpack [documentation webpack init](https://webpack.js.org/guides/development/#using-webpack-dev-server)

### Added

- npm init -y
- npm install webpack webpack-cli --save-dev
- new file `src/index.js`

```javascript
console.log('hello from webpack');
```

- create `webpack.config.js` file alongside `src` folder

```javascript
const path = require('path');
module.exports = {
  entry = './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist')
  }
}
```

### Changed

- modify `package.json`

```javascript
    "build": "webpack"
```

## [0.2] - 2021-01-17

> Add webpack-dev-server and html-webpack-plugin

### Added

> [documentation webpack dev server](https://webpack.js.org/guides/development/#using-webpack-dev-server)

- `npm install --save-dev webpack-dev-server`
- `npm install --save-dev html-webpack-plugin`

### Changed

- `webpack.config.js`

```javascript

```

- `package.json`

```javascript
  "dev":"webpack-dev-server --open",
```

# Changelog

## [0.3] - 2021-01-17

> Integrating with babel. [babel documents](https://babeljs.io/setup#installation)

### Added

- `npm install --save-dev babel-loader @babel/core`
- `npm install --save-dev @babel/preset-env`
- create `.babelrc` or `babel.config.json` and add

```javascript
{
  "presets": ["@babel/preset-env"]
}
```

### Changed

- `webpack.config.js`

```javascript
  module: {
    rules: [{ test: /\.js$/, exclude: /node_modules/, loader: 'babel-loader' }],
  },
```

- `src/index.js`

```javascript
const foo = (name) => {
  console.log(`Hello ${name}`);
};

foo('Robert');
```

### Errors

- Error: Cannot find module 'webpack-cli/bin/config-yargs'
  ![](./assets/img/err_1png)

  -> webpack-cli v4 doesn't work with webpack-dev-server v3. CHeck your `package.json` file
