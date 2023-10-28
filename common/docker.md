
```bash
docker -v #查看版本
systemctl start docker #启动docker
systemctl stop docker  #停止docker
systemctl restart docker #重启docker
systemctl status docker  #查看docker状态
systemctl enable docker  #开机启动
docker ps #查看正在运行容器
docker ps -a #查看所有容器

#文件拷贝：
#1、从docker容器中拷贝出来
docker cp tomcat:/usr/local/tomcat/webapps/ /usr/local/mysofts/tomcat/
#2、从宿主机考进docker
docker cp /usr/local/mysofts/tomcat/ tomcat:/usr/local/tomcat/webapps/

#交互式命令
#使用docker时不能直接通过路径进入到docker中
#进入命令
docker exec -it <CONTAINER_ID> /bin/bash
#查看日志
docker logs -f -t --tail=100 <CONTAINER_ID>
#退出：
exit
```