# chia安装

chia configure --set-farmer-peer 10.10.10.231:8447

\#添加农田目录 c:\daemon\chia.exe plots add -d Y:\\

\#批量添加农田目录 lsblk | grep 7.3T | awk '{print $7}' > hdd.txt for i in $(cat hdd.txt); do echo $i ; docker exec chia-harvester chia plots add -d $i; done

\#命令启动收割机 c:\daemon\chia.exe start harvester

\#命令关闭收割机 c:\daemon\chia.exe stop harvester 或者 c:\daemon\chia.exe stop all -d

***

### docker run -v /mnt:/mnt -m 8G --cpus 8 odelucca/chia-plotter -t /mnt/d/chia\_temp/ -d /mnt/i/pool/ -c xch1vww5cnu9kgtrcevjaw9nqr3ps4uz3erg9lpq4dakcur9u8nrpq2s5p234z -f a95b4750acc1fbbcddb133e25f5baf3add752a4e2213c39455dd7511ad792bcda5caa492cba1a507b62ffba915a54478 -r 8

full node 全节点 wallet 钱包 plots 农田 farm 农场

chia\_harvester: started chia\_timelord\_launcher: started chia\_timelord: started chia\_farmer: started chia\_full\_node: started chia\_wallet: started

main machine plotting machine harvester machine farmer\_key pool\_key

\#################### cat /root/chia-docker/root/.chia/mainnet/log/debug.log | grep -i 'error'

cat /root/chia-docker/root/.chia/mainnet/log/debug.log | grep eligible

检查旧版本文件 docker exec chia-harvester curl --insecure --cert \~/.chia/mainnet/config/ssl/full\_node/private\_full\_node.crt --key \~/.chia/mainnet/config/ssl/full\_node/private\_full\_node.key -d '{"":""}' -H "Content-Type: application/json" -X POST https://localhost:8560/get\_plots | jq '.plots\[] | select(.pool\_public\_key != null) | .filename'
