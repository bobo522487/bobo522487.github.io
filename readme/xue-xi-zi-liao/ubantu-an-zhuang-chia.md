# ubantu安装chia

VI# 列出磁盘状态

lsblk lsblk -o name,size,type,serial

\#创建文件目录

sudo mkdir /tmp1

sudo mkdir /data1

## 挂载

mount /dev/nvme1n1 /tmp1

\#安装nfs sudo apt-get install nfs-common

\#编辑 vim /etc/fstab #添加到最后一行 10.10.10.18:/volume1/plots /data1 nfs defaults 0 0 mount -a

sudo mount -t drvfs //10.10.10.133/chia /data1

UI to Remote Daemon

## 更改目录Owner，注意不改文件夹权限P盘的时候会报错

ps -ef | grep chia

主机拷贝ca目录到远程收割机 scp -r /root/.chia/mainnet/config/ssl/ca/ root@10.10.10.21:/root/

ubuntu18.04修改网卡名称为eth0 vim /etc/default/grub #GRUB\_CMDLINE\_LINUX="net.ifnames=0 biosdevname=0" grub-mkconfig -o /boot/grub/grub.cfg vim /etc/netplan/01-netcfg.yaml #修改网络配置ens32为eth0
