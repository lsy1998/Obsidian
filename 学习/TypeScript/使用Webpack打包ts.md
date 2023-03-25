
```js
const path = require('path');
const HTMLWebPackPlugin = require('html-webpack-plugin');
const cleanWebPackPlugin = require('clean-webpack-plugin');

module.exports = {
    // 指定入口文件
    entry: './index.ts',
    // 指定打包文件所在路径
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
    },

    // 指定webpack打包要使用哪些模块
    module: {
        // 指定要加载的规则
        rules: [
            {
                // test指定的是规则生效的文件
                test: /\.ts$/,
                // 要使用的loader
                use: 'ts-loader',
                //要排除的文件
                exclude: /node-modules/
            }
        ]
    },

    //配置webpack插件
    plugins:[
        //清除dist
        new cleanWebPackPlugin(),
        new HTMLWebPackPlugin({
            title:'自定义html文件的title',
            //指定一个模板
            // template: '',
        }),
    ],
    //哪些文件可以当作模块引入
    resolve:{
        extensions: ['.js', '.ts', '.jsx']
    }

}
```
