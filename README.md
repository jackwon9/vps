##   【修改时间】  
```bash
timedatectl set-local-rtc 1
timedatectl set-timezone Asia/Shanghai
date
```

  
##   【关闭firewalld防火墙】  
```bash
systemctl disable firewalld
systemctl stop firewalld
systemctl status firewalld
```

  
##   【BBR相关】 https://github.com/ylx2016/Linux-NetSpeed   
```bash
centos：yum install ca-certificates wget -y && update-ca-trust force-enable
debian/ubuntu：apt-get install ca-certificates wget -y && update-ca-certificates
```
```
wget -O tcpx.sh "https://github.com/ylx2016/Linux-NetSpeed/raw/master/tcpx.sh" && chmod +x tcpx.sh && ./tcpx.sh
```
或者Debian系统  
```bash
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```  

   
##   【ccaa安装】  
```bash
bash <(curl -Lsk https://raw.githubusercontent.com/jackwon9/ccaa/master/ccaa.sh)
``` 
 
   
##   【手动安装File Browser文件管理器】 https://www.xiaoz.me/archives/14299  
```bash
wget https://github.com/filebrowser/filebrowser/releases/download/v2.23.0/linux-amd64-filebrowser.tar.gz
tar -zxvf linux-amd64-filebrowser.tar.gz
mv filebrowser /usr/sbin
mkdir /etc/filebrowser/
vi /etc/filebrowser/config.json
```
#复制下面的内容保存到/etc/filebrowser/config.json  
```bash
{
      "address":"0.0.0.0",
      "database":"/etc/filebrowser/filebrowser.db",
      "log":"/var/log/filebrowser.log",
      "port":8080,
      "root":"/",
      "username":"admin"
}
```
#保持在后台运行，执行  
```bash
nohup filebrowser -c /etc/filebrowser/config.json &
```

  
##   【Aria2 一键安装管理脚本 增强版】  https://github.com/P3TERX/aria2.sh       
```bash
apt install wget curl ca-certificates
```

```bash
wget -N git.io/aria2.sh && chmod +x aria2.sh
```

#其他操作  
service aria2 start | stop | restart | status  
配置文件路径：/root/.aria2c/aria2.conf  
  
  
##   【BuyVM Block Storage（数据盘）挂载方法】  https://cyhour.com/1110/  
查看scsi文件名
```bash
ls /dev/disk/by-id/
```

挂载
```bash
mount -o discard,defaults /dev/disk/by-id/scsi-0BUYVM_SLAB_VOLUME-1546 /256
```

开机运行
```bash
echo '/dev/disk/by-id/scsi-0BUYVM_SLAB_VOLUME-1546 /256 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
```

## 【rclone挂载谷歌团队网盘】  https://omo.moe/archives/103/  
```bash
apt-get install fuse
apt-get install rclone
rclone config
```
#挂载Google Drive  
```bash
rclone mount gd:/1 /256/gd --allow-other --allow-non-empty --vfs-cache-mode writes & df -h
```
     
     
## 【v2ray安装】     
```bash
wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/jackwon9/v2ray/main/install.sh" && chmod +x install.sh && bash install.sh
```
在/home/wwwroot/3DCEList/里添加***.txt作订阅链接  
#其他操作  
service v2ray start | stop | restart | status  
其他版本https://github.com/wulabing

#无法启动解决方法
```
vi /etc/systemd/system/v2ray.service
```
```
[Unit]
Description=V2Ray Service
After=network.target nss-lookup.target

[Service]
User=root
CapabilityBoundingSet=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
AmbientCapabilities=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
NoNewPrivileges=true
Environment=V2RAY_LOCATION_ASSET=/usr/local/lib/v2ray/
ExecStart=/usr/local/bin/v2ray run -config /etc/v2ray/config.json
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
还有
```
vi /etc/systemd/system/v2ray@.service
```
```
[Unit]
Description=V2Ray Service
After=network.target nss-lookup.target

[Service]
User=root
CapabilityBoundingSet=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
AmbientCapabilities=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
NoNewPrivileges=true
Environment=V2RAY_LOCATION_ASSET=/usr/local/lib/v2ray/
ExecStart=/usr/local/bin/v2ray run -config /etc/v2ray/%i.json
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
然后
```
systemctl daemon-reload
systemctl restart v2ray
systemctl status v2ray
```


## 【Hysteria安装】 
```bash
bash <(curl -fsSL https://git.io/hysteria.sh)
```


## 【其他指令】  
Debian/Ubuntu：  
```bash
apt-get install fuse
```

Centos：  
```bash
yum install fuse
```
## 【其他】
```bash
apt update
```

```bash
apt-get install wget
```
```bash
apt-get install sudo
```
```bash
apt-get install curl
```

curl: command not found解决方法：
```bash
apt-get update -y && apt-get install curl -y
```
