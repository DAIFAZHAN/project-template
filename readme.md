# webpack
```
pnpm add webpack webpack-cli -D
```

# babel
```
pnpm add @babel/core @babel/preset-env @babel/preset-react babel-loader -D
```

@babel/core 调用Babel的API进行转码

@babel/preset-env 用于解析 ES6+

@babel/preset-react 用于解析 JSX

babel-loader 加载器

## babel.config.json
```
{
  "presets": ["@babel/preset-react", "@babel/preset-env"],
  "plugins": []
}
```
## webpack.dev.config.js
```
const path = require("path");

module.exports = {
  /* 入口 */
  entry: path.join(__dirname, "../src/index.js"),
  /* 输出到dist目录，输出文件名字为bundle.js */
  output: {
    path: path.join(__dirname, "../dist"),
    filename: "bundle.js",
  },
  module: {
    rules: [
      /* cacheDirectory是用来缓存编译结果，下次编译加速 */
      {
        test: /\.(js|jsx)$/,
        use: ["babel-loader?cacheDirectory=true"],
        include: path.join(__dirname, "../src"),
      },
    ],
  },
};
```

# React
```
pnpm add react react-dom
```
demo:
```
// index.js
import React from "react";
import ReactDom from "react-dom";

class Hello extends React.Component {
  render() {
    return <div>开始使用React!</div>;
  }
}

ReactDom.render(<Hello />, document.getElementById("root"));

// dist/index.html
<!doctype html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>

<body>
  <div id="root"></div>
  <script type="text/javascript" src="./bundle.js"></script>
</body>

</html>
```
