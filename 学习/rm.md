 [![Linux 命令大全](https://www.runoob.com/images/up.gif) Linux 命令大全](https://www.runoob.com/linux/linux-command-manual.html)

Linux rm（英文全拼：remove）命令用于删除一个文件或者目录。

### 语法

rm [options] name...

**参数**：

-   -i 删除前逐一询问确认。
-   -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
-   -r 将目录及以下之档案亦逐一删除。

### 实例

删除文件可以直接使用rm命令，若删除目录则必须配合选项"-r"，例如：

# rm  test.txt 
rm：是否删除 一般文件 "test.txt"? y  
# rm  homework  
rm: 无法删除目录"homework": 是一个目录  
# rm  -r  homework  
rm：是否删除 目录 "homework"? y 

删除当前目录下的所有文件及目录，命令行为：

rm  -r  * 

文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。

 [![Linux 命令大全](https://www.runoob.com/images/up.gif) Linux 命令大全](https://www.runoob.com/linux/linux-command-manual.html)

[](https://www.runoob.com/linux/linux-shell-include-file.html) [Shell 文件包含](https://www.runoob.com/linux/linux-shell-include-file.html "Shell 文件包含")

[Nginx 安装配置](https://www.runoob.com/linux/nginx-install-setup.html "Nginx 安装配置") [](https://www.runoob.com/linux/nginx-install-setup.html)

## 

1 篇笔记 写笔记

1.     15202180335
    
      wan***ang-cf@bestpay.com.cn
    
    229
    
    删除当前目录下的所有文件及目录，并且是直接删除，无需逐一确认命令行为：
    
    rm  -rf  要删除的文件名或目录
    
    删除文件名 test.txt:
    
    rm  -rf   test.txt
    
    删除目录 test，不管该目录下是否有子目录或文件，都直接删除:
    
    rm  -rf   test/
    
    15202180335
    
       15202180335
    
      wan***ang-cf@bestpay.com.cn
    
    4年前 (2018-11-26)