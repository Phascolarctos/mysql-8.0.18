# MYSQL_INSTALL UBUNTU-20.04
## MYSQL INSTALL
```
apt update
apt install mysql-server
systemctl status mysql
mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'YOUR_PASSWORD';
```
## SecureInstall
```
mysql_secure_installation
```
## Create User
```
create user 'username'@'%' identified by 'very_strong_passwd';
grant all privileges on *.* to 'username'@'localhost' identified by 'very_strong_passwd'
```
