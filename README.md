# docker

tutorial

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
