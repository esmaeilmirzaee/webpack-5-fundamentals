# Webpack 5 fundamentals

# Changelog

## [0.1] - 2021-01-17

> [documentation webpack init](https://webpack.js.org/guides/development/#using-webpack-dev-server)

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

### Added

> [documentation webpack dev server](https://webpack.js.org/guides/development/#using-webpack-dev-server)

- `webpack-dev-server`

### Changed

- Change item
