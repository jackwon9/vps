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
    "port":6800,  
    "root":"/",  
    "username":"admin"  
}  
#保持在后台运行，执行  
nohup filebrowser -c /etc/filebrowser/config.json  
  
  
【Aria2 一键安装管理脚本 增强版】  
apt install wget curl ca-certificates  
wget -N git.io/aria2.sh && chmod +x aria2.sh  
#其他操作  
service aria2 start|stop|restart|status  
配置文件路径：/root/.aria2c/aria2.conf  
