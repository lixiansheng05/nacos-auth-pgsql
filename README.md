# 简介
Nacos通过集成插件适配pgsql
快速使用
## 1.下载nacos-datasource-plugin-pgsql插件jar：
您可以从最新的稳定版本下载打包好的jar：点此下载

获取前往maven仓库下载：点此下载

也可以自行打包：

~~~
git clone https://github.com/hlinfocc/nacos-datasource-plugin-pgsql.git
cd nacos-datasource-plugin-pgsql/
mvn clean package
~~~


## 2.下载nacos-auth-plugin-extend-pgsql插件jar：
您可以从最新的稳定版本下载打包好的jar：点此下载

获取前往maven仓库下载：点此下载

也可以自行打包（编译打包本插件前请务必先在本地mvn clean install官方源码）：
~~~
git clone https://github.com/hlinfocc/nacos-auth-plugin-extend-pgsql.git
cd nacos-auth-plugin-extend-pgsql/
mvn clean package
~~~
### 3.下载nacos-server
可在nacos的GitHub仓库下载

也可以自行下载nacos源码打包：
~~~
git clone https://github.com/alibaba/nacos.git
cd nacos/
mvn -Prelease-nacos -Dmaven.test.skip=true clean install -U 
echo "打包后的文件位于： ./distribution/target/:"
ls -al ./distribution/target/
~~~
### 3.1配置
在nacos安装目录下新建plugins目录，并将nacos-datasource-plugin-pgsql插件jar放入此目录，目录结构如下：
~~~
nacos/
├── bin
├── conf
├── data
├── plugins
│   ├── nacos-datasource-plugin-pgsql-2.3.0.jar
│   └──nacos-auth-plugin-extend-pgsql-2.3.0.jar
├── target
│   └── nacos-server.jar
~~~
### 3.2配置数据库链接信息
编辑conf/application.properties配置文件
~~~
#*************** Config Module Related Configurations ***************#
### If use MySQL as datasource:
spring.datasource.platform=pgsql
spring.sql.init.platform=pgsql

### Count of DB:
db.num=1

### Connect URL of DB:
db.url.0=jdbc:postgresql://127.0.0.1:5432/nacos?tcpKeepAlive=true&reWriteBatchedInserts=true&ApplicationName=nacos_java
db.user.0=postgres
db.password.0=123456
db.pool.config.driverClassName=org.postgresql.Driver
~~~
# 配置本鉴权插件名字
nacos.core.auth.system.type=nacos_pg
### 3.3创建nacos数据库
nacos-pgsql.sql到PostgreSQL数据库
### 3.4启动nacos服务
单机模式启动：
~~~
cd nacos/
./bin/startup.sh -m standalone
~~~
## 4.许可证
Apache 许可证版本 2.0
