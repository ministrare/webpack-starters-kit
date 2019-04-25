# Webpack 2 starters kit

## Table of content
 * [What is Webpack](#What-is-webpack)
    - [Official documentation](#Official-Documentation)
 * [Setup new project](#Setup-new-project)
    - [File Structure](#File-structure)
 * [Initialise npm](#Initialise-npm)
 * [Install webpack, webpack-cli and webpack-dev-server](#Install-webpack-webpack-cli-and-webpack-dev-server)
 * [Sass compiler, extract-text-webpack-plugin and Babel](#Sass-compiler-extract-text-webpack-plugin-and-Babel)
 * [HTML loader](#HTML-loader)
 * [File-loader](#File-loader)
 * [Multiple HTML files](#Multiple-HTML-files)
 * [Using 3rd Party packages](#Using-3rd-party-packages)
 * [Sources](#Sources)

## What is webpack?
Start by reading the following introduction: [What is Webpack](https://survivejs.com/webpack/what-is-webpack/). \
To go more in detail and with examples: [LevelupTuts - What is webpack](https://www.youtube.com/watch?v=nfmvexyoHXE).

### Official Documentation
To start learning about webpack we need a starting point. \
The best option is to start at the begining, so start open up your browser and start asking our best friend google, where to find the official tutorial by entering the following command:
```
webpack official tutorial
```
Often the first hit will get you to where you want to, in this case: [Official Webpack.js.org documentation - getting started](https://webpack.js.org/guides/getting-started/)
Take the time to read true at least the first couple of chapters.

## Setup new project
Time to dig into the practical stuff.. \

@TODO

### File structure
@TODO

## Initialise npm

Initialise npm into your project
```
npm init -y
```

## Install webpack, webpack-cli and webpack-dev-server
Install webpack, webpack-cli and webpack-dev-server into your project
```
npm i -D webpack webpack-dev-server webpack-cli
```

Generate a webpack.config.js file to store the workflow settings for webpack \
add the following to this file:
```ecmascript 6
const path = require('path');

module.exports = {
    entry: './src/js/app.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
        publicPath: '/dist'
    },
};
```

## Sass compiler, extract-text-webpack-plugin and Babel
install the dependencies for the sass compiler, extracting css into separate css file by the extract-text-webpack-plugin and babel compiler for the es6 js:
```
npm install sass-loader node-sass css-loader @babel/core @babel/preset-env extract-text-webpack-plugin@next babel-loader --save-dev
```
add the following to the top off the webpack.config.js file:
```ecmascript 6
const ExtractTextPlugin = require('extract-text-webpack-plugin');

const extractPlugin = new ExtractTextPlugin({
    filename: 'main.css'
});
```

add the following rules after the ouput methode to the webpack.config.js file:
```ecmascript 6
    module: {
        rules: [
            {
                test: /\.js$/,
                use: [
                    {
                        loader: "babel-loader",
                        options: {
                            presets: ['@babel/preset-env']
                        }
                    }
                ]
            },
            {
                test: /\.scss$/,
                use: extractPlugin.extract({
                    use: ['css-loader', 'sass-loader']
                })
            }
        ]
    },
    plugins: [
        extractPlugin
    ],
```

## HTML loader & File-loader
```
npm i -D html-loader html-webpack-plugin file-loader
```

```
npm i -d clean-webpack-plugin
```

## Multiple-HTML-files
```

```


## Using-3rd-party-packages

### Sources
 - [survivejs.com - What is Webpack](https://survivejs.com/webpack/what-is-webpack/)
 - Youtube: [LevelupTuts - What is webpack](https://www.youtube.com/watch?v=nfmvexyoHXE)
 - [Webpack.js.org - Official Webpack Tutorial](https://webpack.js.org/guides/getting-started/)
 - Youtube: [Academind - Webpack 2 basic tutorial](https://www.youtube.com/watch?v=GU-2T7k9NfI&list=PL55RiY5tL51rcCnrOrZixuOsZhAHHy6os)
 - Youtube: [Academind - Youtube channel](https://www.youtube.com/channel/UCSJbGtTlrDami-tDGPUV9-w/playlists)