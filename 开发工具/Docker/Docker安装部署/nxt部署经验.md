1. 安装docker
  - yum 添加阿里repo源
  - 使用yum安装docker时可能会出现找不到镜像的404错误, 需要更改repo 文件中的releace占位符, 改为当前系统版本
2. 使用docker私库的时候, 需要将私库地址添加如/etc/docker/daemon.json 文件中
如: "registry-mirrors": ["http://4e70ba5d.m.daocloud.io","https://docker.mirrors.ustc.edu.cn","https://6kx4zyno.mirror.aliyuncs.com"],
添加完成后需要停掉docker, 并且重新加载daemon,  systemtcl stop docker, systemctl daemon-reload, systemctl start docker;

docker login 仓库名
如：docker login registry.env.yns12316.cn

示例账户密码
abc
123456

3. 拉取镜像时, 当镜像过多, 可以使用docker-compose 进项拉取 docker-compose pull
4. 多个容器需要互相访问时, 需要创建一个网络 docker network create NETWORK_NAME;
5. 在使用docker启动项目时, 因为在docker中有映射用户到宿主机中, 所以需要找到容器中运行的用户id与其对应的宿主机用户id, 并且将
   容器卷映射的宿主机目录的读写执行权限赋予改用户/或将该目录的用户改为该 用户id对应的用户;
6. 部署minio时, 需要添加minio的policy, 添加匿名读取, 才能直接通过bucket + file 访问文件