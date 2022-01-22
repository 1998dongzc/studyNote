# Docker笔记

## 常用命令

----

#### docker run/create

从镜像启动一个容器

run = create + start

create 用法与 run相同 只是使用create后需要start启动

```shell
运行mysql
#docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123 --name mysql01 mysql:5.7

-d 后台运行
-p 端口映射 服务器端口：容器应用端口
-P 随机端口映射
-v 卷挂载   服务器目录：容器目录  （可以多个挂载）
--volumes-from 容器 ，将容器数据与其他容器绑定，类似于共享硬盘思想
-e 容器配置
--name 容器命名
--restart 当容器被停止后自动重新启动 docker stop停止的容器不会被重启
有三种重启模式 always、unless-stopped、on-failure
always stop停止后 重启docker服务 always策略的容器会重启
unless-stopped stop停止后 重启docker服务 unless-stopped策略的容器不会重启
on-failure 非正常退出，容器会重启，可以用on-failure:time指定重启time次
```

---

#### docker ps

查看运行中的镜像

```shell
无参数 只查看运行中的容器
-a 查看所有容器包括为运行的容器
-q 只显示容器Id
-l 查看最新所有创建的容器
-n num 查看最新num个创建的容器
```

----

#### docker rm/rmi

docker rm id/name 通过id或别名删除本地容器

docker rmi 删除本地镜像

```shell
-f 强制删除
```

----

#### docker kill / stop / start / restart / pause / unpause

docker kill 暴力停止容器 发出停止信号 容器立即停止

docker stop 优雅停止容器 发出停止信号 容器处理完停止相关的工作再停止容器

docker start 启动一个停止的容器

docker restart 重启一个停止或已经启动容器

docker pause 暂停一个容器的服务

docker unpause 回复一个容器的服务

----

#### docker exec

docker exec 容器 /bin/bash 对运行中的容器执行命令

```shell
-it 对容器开启一个伪终端
# docker exec -it mysql01 /bin/bash
```

----

####  docker logs

docker logs 容器  查看容器的日志

```shell
-t 显示时间戳
-tail num 显示最后num条日志
--since time 显示time开始时间的所有日志
-f 持续跟踪查看日志
# docker logs --since 2021-07-20 -f mysql01 
```

----

#### docker inspect

docker inspect 容器  获取容器docker应用中的源信息

----

#### DockerFile

###### 基础知识：

1. 命令关键字都是大写
2. 命令文件从上倒下一步一步运行
3. 每一层命令都是一层镜像
4. #为注释内容

DockerFile用于开发部署项目打包成新镜像

###### 命令：

```shell
FROM 			--指定基础镜像
MAINTAINER 		--指定镜像编写者信息  姓名+镜像
RUN  			--镜像构建构建时需要运行的命令
ADD  			--添加工具的压缩包  如Tomcat
WORKDIR  		--镜像工作目录 
VOLUME  		--设置挂载卷
EXPOSE 			--指定暴露端口 同等与 run命令的 -p参数
CMD   			--指定容器启动的运行的命令 只运行最后一个  会被替换
ENTRYPOINT 		--指定容器启动的运行的命令，可以追加命令
ONBUILD			--构建一个被继承DOckerFile后 触发命令
COPY			--将文件拷贝到镜像中
ENV				--构建时设置容器的环境
```

## 常用方法

----

1.对已有的生产镜像，修改内容后，重新上传可能会造成原镜像标签与新镜像标签重复的情况，此时先可以先利用

```shell
docker images --digests <镜像名>

#获取后的散列值
sha256:99e0989e7e3797cfbdb8d51a19d32c8d286dd8862794d01a547651a896bcf00c
```

获取本地镜像的唯一hash散列值，随后删除本地镜像，再利用获取到的散列值拉取到本地

```shell
docker pull <镜像名>@<hash散列值>
```

这样就可以解决本地镜像标签冲突
