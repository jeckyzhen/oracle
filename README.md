# oracle
免费甲骨文搭建V2ray

甲骨文官网：https://www.oracle.com/cn/cloud/free/

①获取root权限：
sudo -i

② 

V2ray一键安装指令：

bash <(curl -s -L https://git.io/v2ray.sh)


一路全部默认即可

 输入代码生成Vmess URL 链接：v2ray url


备注非常：重要

使用Oracle Cloud free 免费云搭建了v2ray /  shadowsockR， 在 子网 -> 安全列表 -> 入网规则 里也打开了对应的端口，但还是无法科学上网。

原来oracle cloud与 aws等云不同，需要关闭防火墙或iptable。


解决方法：

centos操作如下：

#停止firewall
systemctl stop firewalld.service
#禁止firewall开机启动
systemctl disable firewalld.service
#关闭iptables
service iptables stop
#去掉iptables开机启动
chkconfig iptables off

oracle Linux操作如下：
#停止firewall
systemctl stop firewalld.service
#禁止firewall开机启动
systemctl disable firewalld.service

ubuntu操作如下：
#Oracle自带的Ubuntu镜像默认设置了Iptable规则，关闭它
apt-get purge netfilter-persistent
reboot
#强制删除
rm -rf /etc/iptables && reboot
