# Set up React project with Webpack
Setting up React project with webpack

*With npm
```
git clone https://github.com/ngocducedu/ReactWebpack.git
```
```
cd Learn-WebPack
```
```
npm install
```
```
npm run dev
```
```
npm start 
```

http://localhost:8080/

=============================================================================================
1. 
mkdir minimal-react-boilerplate  // tao foloder
cd minimal-react-boilerplate
npm init -y                      // -y indicate all default condfig should used

2. From root folder .
	mkdir dist
	cd dist
	touch index.html

3. In dist/index.html => push html content

4. Setup Webpack
Use webpack as module bundler 
use webpack-dev-server to serve your bundle app in local enveroment 
need webpack-cli node package to configure webpack setup in configuration file later on

	npm install --save-dev webpack webpack-dev-server webpack-cli

add script additionally to the default to run webpack-dev-server

"start": "webpack-dev-server --config ./webpack.config.js --mode development"

--mode development =>Webpack configurations which came with Webpack 4

Root folder:
	touch webpack.config.js

webpack.config.js  =>
module.exports = {
  entry: [
    './src/index.js'
  ],
  output: {
    path: __dirname + '/dist',
    publicPath: '/',
    filename: 'bundle.js'
  },
  devServer: {
    contentBase: './dist'
  }
};

-Rougly : entry => entry point to bundle
	output => result in a bundle.js  // /dist folder will be used to serve	our app

5. From root folder make /src/index.js
mkdir src
cd src
touch index.js

- src/index.js
 console.log('My Minimal React Webpack Babel Setup');

6. Install Babel for write code in ES6
from root : npm install --save-dev babel-core babel-loader babel-preset-env

use more experimental features in ES6 , which can get activated via stages

from root
npm install --save-dev babel-preset-stage-2

configuration to transform natural React.jsx =-> .js
npm install --save-dev babel-preset-react

7. extract you Babel configuaration in separate .babelrc configuration file
from root: touch .babelrc

=========
React Setup in a Webpack + Babel Project

from root npm install --save react react-dom
(1) setup Webpack to bundle our source files in one file as bundle.js
(2) build our first React root component which uses the entry point id=“app”


=====
Hot module Replacement in react

Help reloading the entire page if change in app

-from root: npm install --save-dev react-hot-loader

-from webpack.config.js -> add    
entry: [
    'react-hot-loader/patch',
    './src/index.js'
],

- in src/index.js => add to bottn file =>> module.hot.accept();



=> npm start

====
Loading css: 
	npm install --save-dev style-loader css-loader

webpack.config.js: add ==>
+   module: {
+     rules: [
+       {
+         test: /\.css$/,
+         use: [
+           'style-loader',
+           'css-loader'
+         ]
+       }
+     ]
+   }

=>import './style.css'
=> src/index.js   :  import './style.css';

npm run build

--
