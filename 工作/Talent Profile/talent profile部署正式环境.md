标签: #talent-profile

> **做好备份**

# 部署前准备

### 1. 代码
#### 修改代码
修改相关配置文件，如后端目录路径，前段baseapi
**vue.config.js**
```js
const port = process.env.port || process.env.npm_config_port || 82 -> 80

target: `http://localhost:8090` -> `http://localhost:8088`,
```

**logback.xml**
```xml
<property name="log.path" value="D:/Skill_Matrix/file/sundry" />
```

**application.yml**
```yml
profile: D:/Skill_Matrix/file/sundry

# 开发环境配置  
server:  
  # 服务器的HTTP端口，默认为8080  
  port: 8090 -> 8088
```

**.env.production**
```
# 管理系统/生产环境//cngua01ms084:9008 //cngua01ms065:9008
VUE_APP_BASE_API = '//cngua01ms065:9008'
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

