# prometheus学习笔记

1. 部署

prometheus docker run -d -p 9090:9090 -v /root/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

grafana

alertmanager

2. 部署Node-exporter docker run -d --net="host" --pid="host" -v "/:/host:ro,rslave" quay.io/prometheus/node-exporter:latest --path.rootfs=/host
3. 部署Cadvisor-exporter docker run --volume=/:/rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8080:8080 --detach=true --name=cadvisor --net=host google/cadvisor:latest

\################### curl -X POST http://10.10.10.239:9090/-/reload curl -X POST http://172.16.109.26:9091/-/reload curl -X POST http://192.168.10.50:9090/-/reload ################### 删除指定 Metric 名称和特定 label 名称的全部数据 curl -X POST -g 'http://172.16.109.26:9091/api/v1/admin/tsdb/delete\_series?match\[]=total\_plots\_count{hostname="p31"}' ###################

删除所有容器 docker rm `docker ps -a -q`

删除所有镜像 docker rmi `docker images -q`

查找大于100M的文件 find . -type f -size +1000000k

\#开机自启动 systemctl enable docker #查看容器信息 docker inspect \[CONTAINER ID] #进入容器 docker exec -u root -it \[CONTAINER ID] /bin/sh #查看容器日志 docker logs -f \[CONTAINER ID] ————————————————

\####################

remote\_write:

* url: https://prometheus-blocks-prod-us-central1.grafana.net/api/prom/push basic\_auth: username: 124403 password: eyJrIjoiMzUzOGMxN2YwMDA0OTQyM2ZjOWM5NmM5Zjk2MzA5M2QzNTQ0ZDY3MSIsIm4iOiJwcm9tZXRoZXVzX2JvYm81MjI0ODciLCJpZCI6NTAzNjk0fQ==
