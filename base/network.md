# 网络相关

## 防火墙常用命令

1.查看防火墙状态:
firewall-cmd --state
2.启动防火墙
systemctl start firewalld
3.关闭防火墙
systemctl stop firewalld
4.检查防火墙开放的端口
firewall-cmd --permanent --zone=public --list-ports
5.开放一个新的端口
firewall-cmd --zone=public --add-port=8080/tcp --permanent
6.重启防火墙
firewall-cmd --reload
7.验证新增加端口是否生效
firewall-cmd --zone=public --query-port=8080/tcp
8.防火墙开机自启动
systemctl enable firewalld.service
9.防火墙取消某一开放端口
firewall-cmd --zone=public --remove-port=9200/tcp --permanent
(注:开放端口或取消端口后,重要重启防火墙)

## port操作

查看已经连接的服务端口(ESTABLISHED)
netstat -a
查看所有的服务端口(LISTEN,ESTABLISHED)
netstat -ap
查看指定端口,可以结合grep命令:
netstat -ap | grep 8080
也可以使用lsof命令:
lsof -i:8080
还有一个比较好用的命令,查看**端口:
netstat -lnp | grep 8080
若要关闭使用这个端口的程序,使用kill + 对应的pid
