【修改时间】  
timedatectl set-local-rtc 1  
timedatectl set-timezone Asia/Shanghai  
date  
  
  
【关闭firewalld防火墙】  
systemctl disable firewalld  
systemctl stop firewalld  
systemctl status firewalld  
  
  
【BBR相关】  
centos：yum install ca-certificates wget -y && update-ca-trust force-enable  
debian/ubuntu：apt-get install ca-certificates wget -y && update-ca-certificates  
wget -N "https://github.000060000.xyz/tcp.sh" && chmod +x tcp.sh && ./tcp.sh  
或者Debian系统  
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf  
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf  
sysctl -p  
lsmod | grep bbr  
  
   
【ccaa安装】  
bash <(curl -Lsk https://raw.githubusercontent.com/jackwon9/ccaa/master/ccaa.sh)  
  
   
【手动安装File Browser文件管理器】  
#下载File Browser  
wget https://github.com/filebrowser/filebrowser/releases/download/v2.12.0/linux-amd64-filebrowser.tar.gz  
#解压  
tar -zxvf linux-amd64-filebrowser.tar.gz  
#移动位置  
mv filebrowser /usr/sbin  
#创建配置文件  
mkdir /etc/filebrowser/  
vi /etc/filebrowser/config.json  
#复制下面的内容保存到/etc/filebrowser/config.json  
{  
      "address":"0.0.0.0",  
      "database":"/etc/filebrowser/filebrowser.db",  
      "log":"/var/log/filebrowser.log",  
      "port":8080,  
      "root":"/home",  
      "username":"admin"  
}    
#保持在后台运行，执行  
nohup filebrowser -c /etc/filebrowser/config.json &  
  
  
【Aria2 一键安装管理脚本 增强版】  
apt install wget curl ca-certificates  
wget -N git.io/aria2.sh && chmod +x aria2.sh  
#其他操作  
service aria2 start | stop | restart | status  
配置文件路径：/root/.aria2c/aria2.conf  
  
  
【BuyVM Block Storage（数据盘）挂载方法】  
https://cyhour.com/1110/  


【rclone挂载谷歌团队网盘】  
apt-get install fuse  
apt-get install rclone  
rclone config  
https://omo.moe/archives/103/  

     
【v2ray安装】     
wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/jackwon9/v2ray/main/install.sh" && chmod +x install.sh && bash install.sh  

     
【Linux更新指令】  
https://www.cnblogs.com/qiantan/p/11167276.html  


【其他指令】  
Debian/Ubuntu：apt-get install fuse  
Centos：yum install fuse
