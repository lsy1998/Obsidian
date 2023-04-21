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
