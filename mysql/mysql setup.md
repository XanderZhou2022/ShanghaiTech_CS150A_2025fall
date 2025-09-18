```
docker pull mysql
```

```
docker run --name mysql-cs150 -d \
    -p 127.0.0.1:3306:3306 \
    -e MYSQL_DATABASE=cs150 \
    -e MYSQL_ROOT_PASSWORD=123456 \
    mysql
```

`docker run`

- 表示新建并运行一个容器。

`--name mysql-chinook`

- 给容器起个名字叫 **`mysql-cs150`**，以后可以用这个名字来操作（如 `docker stop mysql-cs150`）。

`-d`

- **detached 模式**，让容器在后台运行。
   （如果不用 `-d`，容器会在前台跑，你的终端就被占住了。）

`-p 127.0.0.1:3306:3306`

- 把 **容器里的 3306 端口**（MySQL 默认端口）映射到 **宿主机的 127.0.0.1:3306**。
- 解释：
  - **左边 `127.0.0.1:3306`** → 宿主机的地址和端口，你在本机访问这里时就能连到容器。
  - **右边 `3306`** → 容器内部 MySQL 服务监听的端口。
- 意思就是：在本机访问 `127.0.0.1:3306`，实际上就是访问容器里的 MySQL。

`-e MYSQL_DATABASE=Chinook`

- 设置一个 **环境变量**，告诉 MySQL 容器在启动时创建一个名为 **`cs150`** 的数据库。

```
docker rm -f mysql-150
```

