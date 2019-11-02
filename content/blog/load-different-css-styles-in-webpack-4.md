---
path: css-styles-webpack
date: 2019-11-02T23:07:12.308Z
title: Load Different CSS Styles in Webpack 4
description: "Building the frontend of your applications can be fun until you are blocked by the little things \U0001F642"
---
Recently, on a personal project I needed to allow multiple CSS styles (.scss, .sass & .css) files to be loaded properly. The app style was using `.scss` but a third party library used in the app required an import of a `.css` file. To resolve this, I had to make a simple change to my Webpack config. 

Interestingly, this was a simple fix after I had resolved it but not it took a bit of figuring out and Stackoverflow visits. Below is the config that resolved the issue:

```js
// Supported file loaders
  module: {
    rules: [
      {
        test: /\.(sa|sc|c)ss$/,
        use: [
          // Creates `style` nodes from JS strings
          'style-loader',
          // Translates CSS into CommonJS
          'css-loader',
          // Compiles Sass to CSS
          'sass-loader',
        ],
      },
    ],
  },
```

The most important section in the above code snippet is the rule test regex `/\.(sa|sc|c)ss$/`.
