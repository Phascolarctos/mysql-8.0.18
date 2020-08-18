# 安装mysql-8.0.18
1.下载，https://dev.mysql.com/downloads/mysql/  
2.解压到指定目录，在D:\EnvRun\mysql-8.0.18-winx64目录下新建my.ini  
```
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=D:\EnvRun\mysql-8.0.18-winx64
# 设置mysql数据库的数据的存放目录
datadir=D:\EnvRun\mysql-8.0.18-winx64\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为utf8mb4
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```
3.cmd进入bin文件夹下  
4.mysqld --initialize --user=root --console 生成密码  
5.mysqld install 安装  
6.net start mysql 启动  
7.mysql -u root -p 登录  
8.ALTER USER 'root'@'localhost' IDENTIFIED WITH MYSQL_NATIVE_PASSWORD BY '新密码';  
9.FLUSH PRIVILEGES;
注意事项：以管理员权限启动cmd，否则第五步报错。
