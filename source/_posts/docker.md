---
title: Docker常用命令
date: 2019-06-15 17:22:50
tags: docker
categories: command
---
## 记录常用docker命令
<!-- more -->
#### docker基本命令
- docker push
    ```
      $ sudo docker login --username=445436928@qq.com registry-vpc.cn-beijing.aliyuncs.com
      $ sudo docker tag [ImageId] registry-vpc.cn-beijing.aliyuncs.com/w_yufan/my_images:[镜像版本号]
      $ sudo docker push registry-vpc.cn-beijing.aliyuncs.com/w_yufan/my_images:[镜像版本号]
    ```
#### docker镜像操作
- mysql
    ```
    docker run --name first-mysql -p 3306:3306 -d -v /opt/docker_v/mysql/my.conf:/etc/mysql/mysql.conf.d/mysqld.cnf -v /opt/docker_v/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root mysql
    docker exec -it first-mysql /bin/bash
    ```
- redis
    ```
    docker run --name first_redis -p 6379:6379 -v /opt/docker_v/redis/data:/data -v /opt/docker_v/redis/redis.conf:/usr/local/etc/redis/redis.conf -d redis redis-server --appendonly yes
    ```
- ssr
    ```
    docker run -d --name ssr -p 8989:8989 malaohu/ssr-with-net-speeder -s 0.0.0.0 -p 8989 -k yf0720 -m rc4-md5 -o http_simple -O auth_sha1_v4
    ```
- mongodb
    ```
    docker run --name mongo01 -p 27017:27017 -v /opt/docker_v/mongo:/data/db -d mongo --auth
    docker exec -it mongo01 /bin/bash
    mongo
    use admin
    db.createUser({user:"root",pwd:"root",roles:[{role:"root",db:"admin"}]})
    exit
    mongo 宿主机ip/admin -uroot -p
    use admin
    db.auth("admin","admin")
    db.createUser({user: "root",pwd: "root",roles: [{ role: "readWrite", db: "admin"}]})
    ```
- java
    ```
    docker run -it --name java02 -p 1001:1001 -v /root/software:/mnt/software java
    ```
- jenkins
    ```
    docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
    ```
- gitlab
    ```
    docker run --detach --hostname gitlab.example.com --publish 443:443 --publish 80:80 --publish 23:22 --name gitlab --restart always --volume /srv/gitlab/config:/etc/gitlab --volume /srv/gitlab/logs:/var/log/gitlab --volume /srv/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest
    ```
- zookeeper
    ```
    docker pull zookeeper
    docker run --privileged=true -d --name zookeeper --publish 2181:2181  -d zookeeper:latest
    ```