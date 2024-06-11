### MySQL 下载
-----   
##### [` MySQL-8下载地址`](https://cdn.mysql.com//Downloads/MySQL-8.0/mysql-8.0.32-winx64.zip) [`官方地址`](https://dev.mysql.com/downloads/mysql/)

### 配置 MySQL  
-----   
#### 将压缩包解压至任意盘 (本教程以 E 盘作为解压地址)

![[ASLant_Images/fec79ac4d074e946072d91a8fca88f5b_MD5.jpg]]

![[ASLant_Images/e84018e32dd95e5bb1a7df3441aeda7b_MD5.jpg]]

#### 双击进入到 ` mysql\bin ` 目录

![[ASLant_Images/a078496b51020adcd010c30eded7284d_MD5.jpg]]

#### 将地址复制，打开系统环境变量，将 bin 目录添加进去  
![[ASLant_Images/058fc0d34870684be0bb0ebd2908b996_MD5.gif]]    


#### 添加配置文件 ` my.ini `  

##### 将以下内容复制，把 mysql 的安装地址，改为自己的 mysql 解压路径如 `E:\mysql`   

```SQL
[client]
# 设置mysql客户端默认字符集
default-character-set=utf8 
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=E:\mysql
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB   
``` 
![[ASLant_Images/a5dd1536439f38d4cf5d285f653a9729_MD5.jpg]]   

![[ASLant_Images/e7950ce23e6b76e5b69f9ab08604ade1_MD5.jpg]]   

--------    

**以下命令请使用管理员模式在终端执行**    

![[ASLant_Images/c20746433a6df0af46efdcae29e53050_MD5.jpg]]   
![[ASLant_Images/888cd928e2bac7ee79746f69a7c55101_MD5.jpg]]   
![[ASLant_Images/4e4c1c6efeb02d031840273134c3f950_MD5.jpg]]   

#### 初始化数据库

```SQL
mysqld --initialize --console
``` 
![[ASLant_Images/18820c404fc8c2a9627cce24d29939cf_MD5.jpg]]   

#### 安装服务
```SQL
mysqld install
``` 
![[ASLant_Images/f80acba816b3f571af630f8378dd8683_MD5.jpg]]   

#### 启动服务
```SQl
net start mysql
``` 
![[ASLant_Images/3ab9924f9c536a4fe3caf7e8ba386aab_MD5.jpg]]   

#### 登录
```SQL
mysql -u root -p
``` 
![[ASLant_Images/8474d8a223799b1ee443fc1b3c20b50c_MD5.jpg]]   

#### 更改密码
```SQL
ALTER USER 'root'@'localhost' IDENTIFIED BY '12345'; //修改密码为12345 
``` 
![[ASLant_Images/6a2c70586b0c9ed2ef590031f0b41f07_MD5.jpg]]   

#### 使用完毕后关闭后台服务
```SQL
net stop mysql
```
![[ASLant_Images/2ed2a3ee37be08667a5117ebb1421d89_MD5.jpg]]   
