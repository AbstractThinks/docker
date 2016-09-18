# docker
[中文文档](http://www.widuu.com/docker/)

tutorial


##概念
###镜像
1. 镜像ID－－    每个镜像有一个唯一的id

2. 镜像TAG－－    每个镜像可以打上一个或多个tag

3. Repository：TAG －－   唯一标示了一个镜像

###容器
创建的容器在 `/var/lib/docker/aufs/mnt/` 目录中

创建容器步骤

1. 先从镜像目录复制出一个目录a

2. 容器a的进程chroot到目录a下

###修改并保存镜像

1. 保存容器的修改 docker commit 容器id 命名（可通过docker ps －l获取修改后容器的id）

	>例：docker commit 698 learn/ping 

2. 提交到dockerhub上  docker push 容器名

	>例：docker push learn/ping
	



##基础命令

```python

# 用于检查Docker的安装是否正确
docker info

# 创建容器（镜像）  busybox为预先构建的镜像
# busybox是一个最小的libux系统
sudo docker pull busybox

# 执行
docker run busybox /bin/echo Hello Docker

# 以后台进程的方式运行
sample_job=$(docker run -d busybox /bin/sh -c "while true; do echo Docker; sleep 1; done")

docker logs $sample_job

# 停止
docker stop $sample_job

# 重启
docker restart $sample_job

# 移除
docker stop $sample_job
docker rm $sample_job

# 帮助
docker help

# 将容器保存为镜像
docker commit $sample_job job1

# 查看镜像列表
docker images

# 查找registry中的镜像
docker search (image-name)

# 查看镜像历史版本
docker history (image-name)

# 将镜像推送到reistry
docker push （image-name)

```

# 容器修改与保存

```python
# 查看正在运行的容器列表
docker ps

# 查看容器详细信息
docker inspect  容器名

# 查看修改后容器的id
docker ps -l

# 保存修改后的容器
docker commit 修改后容器ID 容器重命名（例：docker commit 698 learn/ping）

```

# 删除镜像与容器

```python
# 停止所有的container，这样才能够删除其中的images：

docker stop $(docker ps -a -q)

# 如果想要删除所有container的话再加一个指令：

docker rm $(docker ps -a -q)

# 查看当前有些什么images

docker images

# 删除images，通过image的id来指定删除谁

docker rmi <image id>

# 想要删除untagged images，也就是那些id为<None>的image的话可以用

docker rmi $(docker images | grep "^<none>" | awk "{print $3}")

# 要删除全部image的话

docker rmi $(docker images -q)

```
