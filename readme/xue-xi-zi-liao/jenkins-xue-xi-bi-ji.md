# jenkins学习笔记

## 启动jenkins docker

docker run\
\-v /usr/bin/docker:/usr/bin/docker\
\-v /var/run/docker.sock:/var/run/docker.sock\
\-v /home/ubuntu/myjenkins/jenkins\_home/:/var/jenkins\_home\
\-u root\
\-d --name jenkins\
\-p 8120:8080\
jenkins/jenkins:jdk11

## 查看token命令

cat /var/jenkins\_home/secrets/initialAdminPassword

## 启动测试docker, 挂载allure报告目录

docker run\
\-v /home/ubuntu/myjenkins/jenkins\_home/beifan/:/app/.allure\_results/\
\--shm-size 2G ccr.ccs.tencentyun.com/beifan/ui\_framework:v1
