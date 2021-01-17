# Webpack 5 fundamentals

# Changelog

### [0.1] - 2021-01-17

> Initialisation of webpack [documentation webpack init](https://webpack.js.org/guides/development/#using-webpack-dev-server)

##### Added

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

##### Changed

- modify `package.json`

```javascript
    "build": "webpack"
```

### [0.2] - 2021-01-17

> Add webpack-dev-server and html-webpack-plugin

##### Added

> [documentation webpack dev server](https://webpack.js.org/guides/development/#using-webpack-dev-server)

- `npm install --save-dev webpack-dev-server`
- `npm install --save-dev html-webpack-plugin`

##### Changed

- `webpack.config.js`

```javascript

```

- `package.json`

```javascript
  "dev":"webpack-dev-server --open",
```

##### Changelog

### [0.3] - 2021-01-17

> Integrating with babel. [babel documents](https://babeljs.io/setup#installation)

##### Added

- `npm install --save-dev babel-loader @babel/core`
- `npm install --save-dev @babel/preset-env`
- create `.babelrc` or `babel.config.json` and add

```javascript
{
  "presets": ["@babel/preset-env"]
}
```

##### Changed

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

### [0.4] - 2021-01-17

> Handle css files []()

##### Added

- 1 `npm install --save-dev style-loader css-loader`
- 2 `npm install --save-dev sass sass-loader`
- 4 `src.main.scss`

```sass
$bodyColour: red;

body{
  background-color: $bodyColour;
}
```

- 5 DO not forget to import it into your `index.js`.

##### Changed

- 3 `webpack.config.js`

```javascript
{test: /\.scss$/i, use:['style-loader', 'css-loader', 'sass-loader']}
```

### [0.5] - 2021-01-17

> Integrating `postcss-loader`

##### Added

- 1 `npm install --save-dev postcss-loader`
- 2 `npm install --save-dev cssnano autoprefixer rucksack-css`
- 3 `npm install --save-dev mini-css-extract-plugin`
- 4 `touch postcss.config.css`

```javascript
module.exports = {
  plugins: {
    autoprefixer: {},
    cssnano: {},
    'rucksack-css': {},
  },
};
```

- 6 create `.browserslistrc`

```
last 2 years
> 1%
not dead
```

##### Changed

- 5 `webpack.config.js`

```javascript
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

{
  test: /\.scss$/i,
  use: [
    {
      loader: MiniCssExtractPlugin.loader,
      options: {
        hmr: process.env.NODE_ENV === 'development',
      },
    },
    ***~~'style-loader',~~
    'css-loader',
    'postcss-loader',
    'sass-loader',***
  ]
}

plugins: [
  // This plugin extracts css file from js files and put them in the appropriate named files.
  new MiniCssExtractPlugin({
    filename: '[name].css'
  })
],
```

**_~~'style-loader'~~,'css-loader','postcss-loader','sass-loader',_**

- 7 `src/main.scss`

```
body {
  display: grid;
  transition: all .5s;
  user-select: none;
  background: linear-gradient(to bottom, white, orange);
  font-size: responsive;
}
```

## Errors

- Error: Cannot find module 'webpack-cli/bin/config-yargs'
  ![](./assets/img/err_1.png)

:: webpack-cli v4 doesn't work with webpack-dev-server v3. CHeck your `package.json` file

- No 'hmr' option ![](./assets/img/err_2.png)

:: Note: HMR is automatically supported in webpack 5. No need to configure it.

- No template for dependency: CssDependency ![](./assets/img/err_3.png)

:: You forgot to load `MiniCssExtractPlugin` into your `webpack.config.js` file.

## Indexes

1. `cssnano`: minimises the css file
2. `.browserslistrc`: specifies supported browsers
