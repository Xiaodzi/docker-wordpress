# wordpress打包镜像
## 方法一
直接使用以下命令拉起容器
```
docker-compose up -d
```

## 方法二

运行打包命令
```
docker build -t wordpress:1.0 .
```
拉起容器
```
docker run -d -p 9090:80 -v /local/folder:/www/wwwroot/demo/docker-wordpress -e "DB_HOST=127.0.0.1:3306" -e "DB_NAME=wordpress" -e "DB_USER=wordpress" -e "DB_PASSWORD=wordpress" -e "FS_METHOD=direct" wordpress:1.0

```
每个命令含义如下：
- -d：在后台运行容器
- -p 9090:80：将主机的 9090 端口映射到容器的 80 端口
- -v /local/folder:/www/wwwroot/demo/docker-wordpress：将本地文件夹挂载到容器中的指定路径
- -e "DB_HOST=127.0.0.1:3306"：设置名为 DB_HOST 的环境变量
- -e "DB_NAME=wordpress"：设置名为 DB_NAME 的环境变量
- -e "DB_USER=wordpress"：设置名为 DB_USER 的环境变量
- -e "DB_PASSWORD=wordpress"：设置名为 DB_PASSWORD 的环境变量
- -e "FS_METHOD=direct"：设置名为 FS_METHOD 的环境变量
- demo:1.0：要运行的容器的名称和版本号