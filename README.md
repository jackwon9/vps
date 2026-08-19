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
wget https://github.com/filebrowser/filebrowser/releases/download/v2.22.2/linux-amd64-filebrowser.tar.gz
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

##【Debian修改DNS】
```
https://www.vdj.me/archives/252.html
```
