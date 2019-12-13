# BUILD WEB APPS WITH WEBPACK

[Webpack](https://webpack.js.org/) is specifically designed to build web applications. In [Gulp](http://www.gulpjs.com), we write Javascript to drive the built system, so this involve writing gulpfile and a bunch of tasks. With webpack, we write configuration file and then add new functionality by using plugins and loaders. Even in some cases no extra configuration is required. We just type `webpack`in the command line with argument for the source file path, and it will build the project.

These are the advantages of using Webpack:

- easily and quickly setup build system that support incremental build
- the build system does not build the entire project when a file change. Therefor the builds are faster

## Using bundles and plugins

Let's define the terminology webpack uses:

- **plugings** are used to change the behavior of the build process. E.g. Automatically uploading assets to [Amazon S3](https://www.npmjs.com/package/webpack-s3-plugin) or removing duplicate files from the output. Plugins are instance of classes that hook into Webpack's more low level API.
- **loaders** are transformations that are applied to resource files. E.g Convert SASS to CSS, or ES2015 to ES5. Loaders are functions that transform input source text into output.

Examples: 

- If we need to convert React code, CoffeScript, SASS or any other transpiled languages, we use **loaders**
- If need to instrument your JavaScript or manipulate a sets of files in some ways, we use **plugins**

We will see how to use webpack with babel loader to convert React ES2015 project to browser-friendly bundle.

## Configuring and running webpack

We are going to re-create the React example from my repo on Gulp [OpenTechConsult/gulpexample](https://github.com/OpenTechConsult/gulpexample) by using **Webpack**

To get started install React this project

> `npm init`   : to initialize a Node project <br>
> `npm install --save react react-dom`  : install React and React-Dom in the project  <br>
> `npm install --save-dev webpack babel-loader @babel/core` : install webpack and loaders <br>
> `npm install --save-dev @babel/preset-env @babel/preset-react` : install 

The last line install Babel's 2015 plugin and the React loader for babel.

Next we need to create a file called **webpack.conf.js** that instructs webpack on : 

- where to find the input files,
- where to write the output
- what loaders to use

We are going to use babel-loader and some additional settings for React.
