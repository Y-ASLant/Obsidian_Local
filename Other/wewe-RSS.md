[[../ASLant_Files/71f85d5cfbee1319073529cd3bc9b257_MD5.jpg|Open: 71f85d5cfbee1319073529cd3bc9b257_MD5.jpg]]
# 公众号以 RSS 形式订阅

### 拉取 Docker 镜像
```sh
docker run -d \
--name wewe-rss \
-p 4000:4000 \
-e DATABASE_TYPE=sqlite \
-e AUTH_CODE=123567 \
-v $(pwd)/data:/app/data \
cooderl/wewe-rss-sqlite:latest
```

### 创建 MySQL_Docker 网络

```shell
docker network create wewe-rss
```

### 启动 MySQL 数据库

```shell
docker run -d \
  --name db \
  -e MYSQL_ROOT_PASSWORD=123567 \
  -e TZ='Asia/Shanghai' \
  -e MYSQL_DATABASE='wewe-rss' \
  -v db_data:/var/lib/mysql \
  --network wewe-rss \
  mysql:latest --default-authentication-plugin=mysql_native_password
```

### 启动 Server

```shell
docker run -d \
  --name wewe-rss \
  -p 4000:4000 \
  -e DATABASE_URL='mysql://root:123456@db:3306/wewe-rss?schema=public&connect_timeout=30&pool_timeout=30&socket_timeout=30' \
  -e AUTH_CODE=123567 \
  --network wewe-rss \
  cooderl/wewe-rss:latest
```

### 访问地址 `ip:4000`

> [!ERROR] 默认端口 4000
![[ASLant_Images/71f85d5cfbee1319073529cd3bc9b257_MD5.jpg]]
[](../ASLant_Files/71f85d5cfbee1319073529cd3bc9b257_MD5.jpg)[[ASLant_Images/71f85d5cfbee1319073529cd3bc9b257_MD5.jpg|Open: 71f85d5cfbee1319073529cd3bc9b257_MD5.jpg]]
# 公众号以 RSS 形式订阅

### 拉取 Docker 镜像
```sh
docker run -d \
--name wewe-rss \
-p 4000:4000 \
-e DATABASE_TYPE=sqlite \
-e AUTH_CODE=123567 \
-v $(pwd)/data:/app/data \
cooderl/wewe-rss-sqlite:latest
```

### 创建 MySQL_Docker 网络

```shell
docker network create wewe-rss
```

### 启动 MySQL 数据库

```shell
docker run -d \
  --name db \
  -e MYSQL_ROOT_PASSWORD=123567 \
  -e TZ='Asia/Shanghai' \
  -e MYSQL_DATABASE='wewe-rss' \
  -v db_data:/var/lib/mysql \
  --network wewe-rss \
  mysql:latest --default-authentication-plugin=mysql_native_password
```

### 启动 Server

```shell
docker run -d \
  --name wewe-rss \
  -p 4000:4000 \
  -e DATABASE_URL='mysql://root:123456@db:3306/wewe-rss?schema=public&connect_timeout=30&pool_timeout=30&socket_timeout=30' \
  -e AUTH_CODE=123567 \
  --network wewe-rss \
  cooderl/wewe-rss:latest
```

### 访问地址 `ip:4000`

> [!ERROR] 默认端口 4000
![[ASLant_Images/71f85d5cfbee1319073529cd3bc9b257_MD5.jpg]]
