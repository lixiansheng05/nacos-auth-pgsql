# 简介
Nacos通过集成插件适配pgsql
快速使用
## 1.下载
 [直接下载](https://github.com/lixiansheng05/nacos-auth-pgsql/releases)
## 2.创建nacos数据库
将pgsql-schema.sql导入到PostgreSQL数据库
## 3.配置数据库
### Windows
编辑conf/application.properties配置文件
~~~
db.url.0=jdbc:postgresql://IP:5432/menhu?currentSchema=nacos
db.user.0=用户名
db.password.0=密码
db.pool.config.driverClassName=org.postgresql.Driver
~~~
### Liunx
编辑docker-compose.yml配置文件
##### 注：Liunx一般用于生产环境，需要配置Nacos鉴权信息，不懂得可以去Nacos官网学习。
~~~
- DATABASE_SERVICE_HOST=jdbc:postgresql://***:5432/menhu?currentSchema=nacos
- DATABASE_SERVICE_USER=用户名
- DATABASE_SERVICE_PASSWORD=密码
- DATABASE_DRIVER_CLASS_NAME=org.postgresql.Driver
  #开启Token缓存功能 
- NACOS_AUTH_CACHE_ENABLE=true
  #用于替换useragent白名单的身份识别
- NACOS_AUTH_IDENTITY_KEY=
- NACOS_AUTH_IDENTITY_VALUE=
  #用于生成用户登陆临时accessToken所使用的密钥
- NACOS_AUTH_TOKEN=
~~~
## 4.启动
单机模式启动：
### Windows
~~~
双击：/bin/startup.cmd
~~~
### Liunx
~~~
sh start.sh
~~~
