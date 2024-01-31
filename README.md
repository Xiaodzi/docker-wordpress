# wordpress打包镜像
## 方法一
直接使用以下命令拉起容器
```
docker-compose up -d
```

## 方法二

运行打包命令
```
docker build -t wordpress .
```
拉起容器
```
docker run -d --name wordpress -p 80:80 -p 3306:3306 -e WORDPRESS_DB_HOST=127.0.0.1 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=root -e WORDPRESS_DB_NAME=wordpress -v /data/www/wordpress:/var/www/html
```
每个命令含义如下：
- docker run: 运行 Docker 容器的命令。
- -d: 在后台运行容器（以分离模式）。
- --name wordpress: 为容器指定一个名称为 wordpress。
- -p 80:80: 将容器的 80 端口映射到主机的 80 端口，允许通过主机的 80 端口访问容器中的服务。
- -p 3306:3306: 将容器的 3306 端口映射到主机的 3306 端口，允许通过主机的 3306 端口访问容器中的服务。
- -e WORDPRESS_DB_HOST=127.0.0.1: 设置名为 WORDPRESS_DB_HOST 的环境变量，指定 WordPress 数据库的主机为 127.0.0.1。
- -e WORDPRESS_DB_USER=root: 设置名为 WORDPRESS_DB_USER 的环境变量，指定 WordPress 数据库的用户名为 root。
- -e WORDPRESS_DB_PASSWORD=root: 设置名为 WORDPRESS_DB_PASSWORD 的环境变量，指定 WordPress 数据库的密码为 root。
- -e WORDPRESS_DB_NAME=wordpress: 设置名为 WORDPRESS_DB_NAME 的环境变量，指定 WordPress 数据库的名称为 wordpress。
- -v /data/www/wordpress:/var/www/html: 将本地文件夹 /data/www/wordpress 挂载到容器中的 /var/www/html 目录，实现主机和容器之间的文件共享。