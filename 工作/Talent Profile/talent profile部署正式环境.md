标签: #talent-profile

> **做好备份**

# 部署前准备

### 1. 代码
#### 修改代码
修改相关配置文件，如后端目录路径，前段baseurl
```
D:/Skill_Matrix/file/sundry
```

```
VUE_APP_BASE_API = '//cngua01ms084:9008'
```
修改端口号

```vue.config.js
const port = process.env.port || process.env.npm_config_port || 82 -> 80

target: `http://localhost:8090` -> `http://localhost:8088`,
```

```application.xml
# 开发环境配置  
server:  
  # 服务器的HTTP端口，默认为8080  
  port: 8090 -> 8088
```


#### 编译前后端
**后端:**
```shell
通过IDEA打包
clean -> compile -> package
```

**前端:**
```shell
npm run build:prod
```



### 2. 数据库
创建dblink(已创建)
创建视图(已创建)

### 3. 上传模版

# 部署步骤
### 1. 关掉测试环境，关掉测试环境定时任务
### 2. 备份正式环境
### 3. 部署前后端

