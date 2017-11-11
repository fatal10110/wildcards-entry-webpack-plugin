# wildcards-entry-webpack-plugin


# quick start

1、 npm install wildcards-entry-webpack-plugin --save-dev

2、webpack.config.js
```
// webpack.config.js
var WildcardsEntryWebpackPlugin = require('wildcards-entry-webpack-plugin');
module.exports = {
    entry: WildcardsEntryWebpackPlugin.entry('./src/js/**/*.entry.js'),
    output: {
        filename: 'dist/[name].js'
    },
    plugins:[
        new WildcardsEntryWebpackPlugin()
    ]
};
```

# how to use




```
// if you have a tree , like this:
.
├── dist
│   └── js
│       └── index.js
├── src
│   ├── a.js
│   └── js
│       └── index.js
└── webpack.config.js
```
### WildcardsEntryWebpackPlugin.entry(wildcards [,watchDir]);
#### @wildcards:

eg 1:    @wildcards: "./src/**/*.js", we will wacth './src', and get chunk name 'js/index'

eg 2:    @wildcards: "./src/js/**/*.js", we will wacth './src/js', and get chunk name 'index'

#### @watchDir (optional)

eg 3:    @wildcards: "./src/js/**/*.js", @watchDir: "./src", we will wacth './src', and get chunk name 'js/index'

##### in watch mode, you can add a entry file in watched dir, wepack will get a new entry as your wildcards.

# dependency
webpack 3

# principle
#### 1.dynamic enry
```
//webpack.config.js
{
    enry: function(){}
}
```
#### 2.watch dir webpack plugin

```
    apply(compiler) {
        compiler.plugin("after-compile", function (compilation, callback) {
            compilation.contextDependencies.push(YOUR_WATCH_DIR);
            callback();
        });
    }
```

# test
```
npm install webpack -g 
git clone ...
cd test
webpack -w
```


# reference

https://github.com/webpack/webpack/issues/370

https://github.com/webpack/webpack/issues/5407

