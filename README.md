# 一个SSH版模仿天猫整站项目

> 本项目使用SSH框架进行系统设计与开发   
> 在经典的SSH解决方案基础上，进行了多次重构，弥补SSH框架本身的不足之处

## 前言
项目包含：

* `tmall_ssh`文件夹为该项目的实际内容
* `tmall_ssh_alltogether`文件夹为该项目源码压缩包和表结构
* `tmall_ssh_withou_install`文件夹为该项目的展示，无需安装JDK,无需配置TOMCAT,无需安装配置数据库。[点此查看说明](#des)


## 运行
1.因为天猫SSH 版本使用了挺多的JDK1.8的新特性，为了正常运行，请务必确认当前java环境是JDK1.8以及以上版本在命令行中输入java -version进行校验


2.为了看到运行效果，还必须导入数据。然后使用MYSQL-FRONT还原tmall_ssh.sql。

**本tmall_ssh.sql 包含17个分类，每种分类下5个产品，总计85件产品。 每个产品下有20余张图片，总计1777张图片，以及属性和属性值等信息。**

考虑到要导入的tmall_ssh.sql文件比较大，通过工具如mysql-front导入的时候，可能会出错导致失败，建议使用命令行导入：

`"D:\tools\MYSQL\mysql-5.1.57-win32\bin\mysql.exe" -u root -padmin --default-character-set=utf8 tmall_ssh < d:\tmall_ssh.sql`

*  账号密码是root，admin，导入数据以及项目运行所使用的账号密码都是这个，如果不是，请将mysql的root账号密码修改为admin

* D:\tools\MYSQL\mysql-5.1.57-win32\bin\mysql.exe 这个路径是我的mysql.exe的路径，根据实际情况换成自己的mysql运行路径

* tmall_ssh.sql下载后，放在 d:\tmall_ssh.sql 这个位置

* tmall_ssh.sql 总计有15715行，所以导入是比较耗时的，预计3-5分钟左右, 视机器配置而定

* 使用命令行方式导入，需要mysql服务器上存在tmall_ssh这个数据库，如果没有请执行以下sql语句：
 
`CREATE DATABASE tmall_ssh DEFAULT CHARACTER SET utf8;
` 
* 导入过程中，有可能提示的 Unknown table engine 'InnoDB'， 这是因为当前数据库未支持InnoDB。 解决办法请参考启动MySQL InnoDB模式

3.解压到e:/project/tmall_ssh

*  一定要解压到e:/project/tmall_ssh,因为其路径依赖是居于这个目录的，倘若放在其他目录，会导致项目jar包导入路径异常

<p id = "des"></p>
---

## 展示
请访问如下地址：

前台
> http://127.0.0.1:3030/tmall_ssh/

后台
> http://127.0.0.1:3030/tmall_ssh/admin

* Tomcat是用了3030端口，避免和其他端口冲突。

* 将jdk集成到tomcat里面(不用客户安装JRE) 或者 tomcat使用指定的jdk方法  

当你不希望在多台机器的环境变量里设置来设置去时，需要在tomcat里指定要使用的jdk，只需要在
`apachetomcat-6.0.29\bin\setclasspath.bat`文件里的开头加上以下代码就可以了(假设jdk在d盘)：

```
set JRE_HOME=d:\jdk5.0       
set JAVA_HOME=d:\jdk5.0
set JSSE_HOME=d:\jdk5.0
```

一种更一劳永逸的方法，可以避免多次修改setclasspath.bat：将jdk放在tomcat目录下，然后将上面的内容更改为：

```
set JRE_HOME="%CATALINA_HOME%\jdk5.0"
set JAVA_HOME="%CATALINA_HOME%\jdk5.0"
set JSSE_HOME="%CATALINA_HOME%\jdk5.0"
```

这样部署项目的时候我们只需要把tomcat放到任意的目录就OK了