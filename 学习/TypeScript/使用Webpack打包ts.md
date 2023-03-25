
```js
const path = require('path');

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
    }
}
```
