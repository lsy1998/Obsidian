
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
                use: [
                    {
                        //指定加载器
                        loader:'babel-loader',
                        options:{
                            presets:[
                                //指定环境的插件
                                "@babel/preset-env",
                                //配置信息
                                {
                                    //要兼容的目标浏览器
                                    targets: {
                                        "chrome":"88",
                                        "ie":"11"
                                    },
                                    //指定core.js的版本
                                    "corejs":"3",
                                    //使用corejs的方式"usage"表示按需加载
                                    "useBuiltIns":"usage"
                                }
                            ]
                        }
                    },
                    'ts-loader'],
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
