# 一个SSH版模仿天猫整站项目

> 本项目使用SSH框架进行系统设计与开发   
> 在经典的SSH解决方案基础上，进行了多次重构，弥补SSH框架本身的不足之处

## 前言
项目包含：

* `tmall_ssh`文件夹为该项目的实际内容
* `tmall_ssh_alltogether`文件夹为该项目源码压缩包和表结构
* `tmall_ssh_withou_install`文件夹为该项目的可执行文件

## 运行
1. 因为天猫SSH 版本使用了挺多的JDK1.8的新特性，为了正常运行，请务必确认当前java环境是JDK1.8以及以上版本在命令行中输入java -version进行校验


2. 为了看到运行效果，还必须导入数据。然后使用MYSQL-FRONT还原tmall_ssh.sql。**本tmall_ssh.sql 包含17个分类，每种分类下5个产品，总计85件产品。 每个产品下有20余张图片，总计1777张图片，以及属性和属性值等信息。**
考虑到要导入的tmall_ssh.sql文件比较大，通过工具如mysql-front导入的时候，可能会出错导致失败，建议使用命令行导入：

 
"D:\tools\MYSQL\mysql-5.1.57-win32\bin\mysql.exe" -u root -padmin --default-character-set=utf8 tmall_ssh < d:\tmall_ssh.sql
 


注: 账号密码是root，admin，导入数据以及项目运行所使用的账号密码都是这个，如果不是，请将mysql的root账号密码修改为admin,参考 修改root密码
注: D:\tools\MYSQL\mysql-5.1.57-win32\bin\mysql.exe 这个路径是我的mysql.exe的路径，根据实际情况换成自己的mysql运行路径
注: tmall_ssh.sql下载后，放在 d:\tmall_ssh.sql 这个位置

注: tmall_ssh.sql 总计有15715行，所以导入是比较耗时的，预计3-5分钟左右, 视机器配置而定
注: 使用命令行方式导入，需要mysql服务器上存在tmall_ssh这个数据库，如果没有请执行以下sql语句：
 
CREATE DATABASE tmall_ssh DEFAULT CHARACTER SET utf8;
 


注：导入过程中，有可能提示的 Unknown table engine 'InnoDB'， 这是因为当前数据库未支持InnoDB。 

