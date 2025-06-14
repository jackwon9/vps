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
wget -O tcp.sh "https://github.com/ylx2016/Linux-NetSpeed/raw/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```
或者Debian系统  
```bash
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```  
   
##   【手动安装File Browser文件管理器】 https://www.xiaoz.me/archives/14299  
```bash
wget https://github.com/filebrowser/filebrowser/releases/download/v2.31.1/linux-amd64-filebrowser.tar.gz
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
mount -o discard,defaults /dev/disk/by-id/scsi-0BUYVM_SLAB_VOLUME-1546 /256/
```

开机运行
```bash
echo '/dev/disk/by-id/scsi-0BUYVM_SLAB_VOLUME-1546 /256/ ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
```


## 【Realm端口转发工具安装教程】  
下载realm-x86_64-unknown-linux-gnu.tar.gz版本解压上传到VPS
https://github.com/zhboner/realm/releases

创建realm配置文件：
```
vi /root/realm.toml
```
复制粘贴以下内容
```
[network]
no_tcp = false
use_udp = true

[[endpoints]]
listen = "0.0.0.0:中转机转发端口"
remote = "落地IP:端口"

[[endpoints]]
listen = "0.0.0.0:54321"
remote = "1.1.1.1:443"
```
创建自启动服务项：
```
vi /etc/systemd/system/realm.service
```
```
[Unit]
Description=realm
After=network-online.target
Wants=network-online.target systemd-networkd-wait-online.service

[Service]
Type=simple
User=root
Restart=on-failure
RestartSec=5s
DynamicUser=true
ExecStart=/root/realm -c /root/realm.toml

[Install]
WantedBy=multi-user.target
```
执行重载系统服务和启动realm服务：
```
systemctl daemon-reload
systemctl enable realm
systemctl start realm
```
```
systemctl stop realm
```
```
systemctl restart realm
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

##   【Dynu綁定動態ip步驟】 
```bash
curl -4 "https://api.dynu.com/nic/update?hostname=gungkaicyuntw.ddnsfree.com&password=huangdadad8964..."
```
```
crontab -e
```
```
*/1 * * * * curl -4 "https://api.dynu.com/nic/update?hostname=gungkaicyuntw.ddnsfree.com&password=huangdadad8964..." >/dev/null 2>&1
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

##【内存清理】
```
echo 1 > /proc/sys/vm/drop_caches
echo 2 > /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
free -m
```

##【Debian替换软件源】
```
https://wph.im/190.html
```

##【screen安装】
```
apt install screen
```
```
screen -S 创建窗口
```
```
screen -r 打开窗口
```

##【ip地址查询】
```
curl 4.ipw.cn
```
```
curl 6.ipw.cn
```

##【iperf3安装】
```
https://www.xxshell.com/2664.html
```

##【流媒体检测】
```
https://github.com/lmc999/RegionRestrictionCheck
```
