## Init (if starting from scratch)

webpack:
`npm i webpack webpack-cli --save-dev`

package.json:
`"scripts": { "build": "webpack --mode production" }`

babel:
`npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev`

.babelrc:
`{ "presets": ["@babel/preset-env", "@babel/preset-react"] }`

webpack.config.js:
```
module.exports = { 
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  }
}
```

react:
`npm -i react react-dom`
##todo react-redux

index files:
`touch src/index.html src/index.js`

webpack-dev-server:
`npm i webpack-dev-server --save-dev`

package.json:
```
"scripts": {
  "start": "webpack-dev-server --open --hot --mode development",
  ...
}
```

index.js:
```
import React from "react";
import ReactDOM from "react-dom";

const App = () => {
  return <div>Hello World!</div>;
};

ReactDOM.render(<App />, document.querySelector("#app"));
```

index.html:
```
<!DOCTYPE html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Title</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>
  <body>
    <section id="app"></section>
  </body>
</html>
```

css:
`npm i css-loader style-loader --save-dev`

HtmlWebPackPlugin:
`npm i html-webpack-plugin html-loader --save-dev`

webpack.config.js:
```
const HtmlWebPackPlugin = require("html-webpack-plugin");
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        },
        {
          test: /\.html$/
          use: [
            {
              loader: "html-loader"
            }
          ]
        }
      }
    ],
    plugins: [
      new HtmlWebPackPlugin({
        template: "./src/index.html",
        filename: "./index.html"
      })
    ]
  }
}
```