# Docker 安装 MySQL

1. 查看可用的 MySQL 版本
访问 MySQL 镜像库地址：https://hub.docker.com/_/mysql?tab=tags 。

此外，我们还可以用 ```docker search mysql``` 命令来查看可用版本.

2. 拉取 MySQL 镜像

这里我们拉取官方的最新版本的镜像：

```$ docker pull mysql:latest```

3. 查看本地镜像

使用以下命令来查看是否已安装了 mysql：

```$ docker images```

4. 运行容器

安装完成后，我们可以使用以下命令来运行 mysql 容器：

```$ docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql```

参数说明：

+ -p 3306:3306 ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 宿主机ip:3306 访问到 MySQL 的服务。
+ MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码。

5. 安装成功

通过 ```docker ps``` 命令查看是否安装成功：


## 查看安装成功

本机可以通过 root 和密码 123456 访问 MySQL 服务。

```
PS C:\Users\Admin\Desktop\Note in git> docker exec -it c66efec4e923 /bin/bash
root@c66efec4e923:/# mysql -h localhost -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 14
Server version: 8.0.22 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> exit
Bye
root@c66efec4e923:/# exit
exit
```