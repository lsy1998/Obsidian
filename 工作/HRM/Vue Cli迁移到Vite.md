#### 官方教程：
[How to Migrate from Vue CLI to Vite - Vue School Articles](https://vueschool.io/articles/vuejs-tutorials/how-to-migrate-from-vue-cli-to-vite/)

vite不支持~（作用类似于@）
```js
换成相对路径
```
vite不支持require
```js
可以用插件，但不好用
```
vite不支持require.context(用于一次性引入多个或动态引入)
```js
require.context 改成 import.meta.globEager
```

#### 在配置中使用环境变量[¶](https://cn.vitejs.dev/config/#using-environment-variables-in-config)

环境变量通常可以从 `process.env` 获得。

注意 Vite 默认是不加载 `.env` 文件的，因为这些文件需要在执行完 Vite 配置后才能确定加载哪一个，举个例子，`root` 和 `envDir` 选项会影响加载行为。不过当你的确需要时，你可以使用 Vite 导出的 `loadEnv` 函数来加载指定的 `.env` 文件。

```js
import { defineConfig, loadEnv } from 'vite'

export default defineConfig(({ command, mode }) => {
  // 根据当前工作目录中的 `mode` 加载 .env 文件
  // 设置第三个参数为 '' 来加载所有环境变量，而不管是否有 `VITE_` 前缀。
  const env = loadEnv(mode, process.cwd(), '')
  return {
    // vite 配置
    define: {
      __APP_ENV__: env.APP_ENV,
    },
  }
})
```
更完整的例子
```js
import { createVitePlugins } from './build/vite/plugins';
import { resolve } from 'path';
import { ConfigEnv, UserConfigExport, loadEnv } from 'vite';

const pathResolve = (dir: string) => {
  return resolve(process.cwd(), '.', dir);
};

// https://vitejs.dev/config/
export default function ({ command }: ConfigEnv): UserConfigExport {
  const root = process.cwd();
  // const env = loadEnv(mode, __dirname)
  const env = loadEnv(command, root);
  return {
    root,
    server: {
      host: true,
      hmr: true,
      proxy: {
        [env.VITE_BASE_URL]: {
          target: env.VITE_TARGET_URL,
          changeOrigin: true,
          secure: false,
          rewrite: (path) =>
            path.replace(new RegExp(`^${env.VITE_BASE_URL}`), '')
        }
      }
    },
  };
}
```
