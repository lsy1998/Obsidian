 [![Linux 命令大全](https://www.runoob.com/images/up.gif) Linux 命令大全](https://www.runoob.com/linux/linux-command-manual.html)

Linux rm（英文全拼：remove）命令用于删除一个文件或者目录。

## 语法

```shell
rm [options] name...
```
**参数**：

-   -i 删除前逐一询问确认。
-   -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
-   -r 将目录及以下之档案亦逐一删除。

## 实例

删除文件可以直接使用rm命令，若删除目录则必须配合选项"-r"，例如：

```shell
rm  test.txt 
```
rm：是否删除 一般文件 "test.txt"? y  
```shell
rm  homework
```
rm: 无法删除目录"homework": 是一个目录  
```shell
rm  -r  homework  
```
rm：是否删除 目录 "homework"? y 

删除当前目录下的所有文件及目录，命令行为：

```shell
rm  -r  * 
```
文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。



## 笔记
删除当前目录下的所有文件及目录，并且是直接删除，无需逐一确认命令行为：
```shell
rm  -rf  要删除的文件名或目录
``` 
删除文件名 test.txt:
```shell
 rm  -rf   test.txt
```
删除目录 test，不管该目录下是否有子目录或文件，都直接删除:
```shell
rm  -rf   test/
```


