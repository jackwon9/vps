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
wget -N "https://github.000060000.xyz/tcp.sh" && chmod +x tcp.sh && ./tcp.sh  
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
#下载File Browser  
```bash
wget https://github.com/filebrowser/filebrowser/releases/download/v2.15.0/linux-amd64-filebrowser.tar.gz  
```
#解压  
```bash
tar -zxvf linux-amd64-filebrowser.tar.gz  
```
#移动位置  
```bash
mv filebrowser /usr/sbin  
```
#创建配置文件  
```bash
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
wget -N git.io/aria2.sh && chmod +x aria2.sh  
```
#其他操作  
service aria2 start | stop | restart | status  
配置文件路径：/root/.aria2c/aria2.conf  
  
  
##   【BuyVM Block Storage（数据盘）挂载方法】  https://cyhour.com/1110/  


## 【rclone挂载谷歌团队网盘】  https://omo.moe/archives/103/  
```bash
apt-get install fuse  
apt-get install rclone  
rclone config  
```

     
## 【v2ray安装】     
```bash
wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/jackwon9/v2ray/main/install.sh" && chmod +x install.sh && bash install.sh  
```
在/home/wwwroot/3DCEList/里添加***.txt作订阅链接  
#其他操作  
service v2ray start | stop | restart | status  
其他版本https://github.com/wulabing  
  
     
## 【Linux更新指令】   https://www.cnblogs.com/qiantan/p/11167276.html  


## 【其他指令】  
```bash
Debian/Ubuntu：apt-get install fuse  
Centos：yum install fuse
```
