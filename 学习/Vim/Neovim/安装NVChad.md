## 前提
安装neovim最新版本
```shell
choco install/upgrade neovim
```
删除`Appdata/local/nvim-data`和`Appdata/local/nvim`里面的文件
## 安装
```shell
git clone https://github.com/NvChad/NvChad $HOME\AppData\Local\nvim --depth 1
```
## 其他问题
因为网络原因可能nvim初始化可能失败，需多次尝试
如果有模块找不到也是网络原因
![[lazy.nvim-9.14.5.zip]]

## lazy.nvim安装插件
修改"C:\Users\lsy\AppData\Local\nvim\lua\custom\plugins.lua"中的代码
例如添加codeium插件，插件加载的相关配置可以查看[官方文档]([folke/lazy.nvim：💤 Neovim的现代插件管理器 (github.com)](https://github.com/folke/lazy.nvim#-plugin-spec))

```lua
  {
    "Exafunction/codeium.vim",
    lazy = false,
    -- event = "InsertEnter",
    -- config = function()
    --   require("better_escape").setup()
    -- end,
  },
```
