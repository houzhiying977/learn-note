---
title: 服务器部署
tags: 服务器
notebook: linux
---
<!-- TOC -->

- [阿里服务器部署](#阿里服务器部署)
    - [自己安装部署环境](#自己安装部署环境)
        - [FTP](#ftp)
        - [JAVA](#java)
        - [MYSQL](#mysql)
        - [TOMCAT](#tomcat)
        - [上传项目](#上传项目)
            - [使用工具](#使用工具)
            - [j2EE项目](#j2ee项目)
            - [maven项目](#maven项目)

<!-- /TOC -->
# 阿里服务器部署

## 自己安装部署环境

### FTP
安装 vsftpd
```
yum install vsftpd -y
```
查看服务启动状态
```
//关闭ftp
systemctl stop vsftpd.service
//启动ftp
systemctl start vsftpd.service
//查看状态
systemctl status vsftpd.service
//查看21端口
netstat -anp|grep 21
```
配置ftp用户（用户名 密码） 访问目录 访问权限
```
//创建ftp用户访问目录
mkdir -p /home/wwwroot/ftptest
//创建用户ftptest
useradd -d /home/wwwroot/ftptest -g ftp -s /sbin/nologin ftptest
//用户ftptest 拥有目录 /home/wwwroot/ftptest 并且有读写功能
chown -R ftptest /home/wwwroot/ftptest
chmod -R 775 /home/wwwroot/ftptest
//为用户ftptest 设置密码
passwd ftptest
//在 chroot_list 加入用户ftptest
vi /etc/vsftpd/chroot_list
```

ftp 客户端ftprush


### JAVA
安装java
```
yum -y install java-1.8.0-openjdk.x86_64
```
查看java版本
```
java -version
```

### MYSQL
```
//创建目录 /temp
mkdir /temp 
// 从社区下载 mysql 安装
cd /temp
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm  
rpm -ivh mysql-community-release-el7-5.noarch.rpm 
//设置密码 admin
mysqladmin -u root password admin
//登录数据库
mysql -uroot -padmin
```

### TOMCAT
首先上传 apache-tomcat-7.0.82.tar.gz 到目录 /home/wwwroot/ftptest
```
//复制tomcat到  /tmp
cp /home/wwwroot/ftptest/apache-tomcat-7.0.82.tar.gz /tmp/apache-tomcat-7.0.82.tar.gz
// 解压 tomcat
tar xzf apache-tomcat-7.0.82.tar.gz
//启动tomcat
/usr/local/tomcat7/bin/startup.sh
//查看8080端口
netstat -anp|grep 8080
//动态查看最后300行 启动日志
tail -300f /usr/local/tomcat7/logs/catalina.out
```

### 上传项目

#### 使用工具
1. Xshell ----- 连接服务器
2. SecureFXPortable ------ 上传下载文件（root权限）
3. ftprush ------ 上传下载文件（分的ftptest 账号）

#### j2EE项目

#### maven项目


