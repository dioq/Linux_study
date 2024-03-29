# 远程连接

安全外壳协议(Secure Shell Protocol,简称SSH)是一种加密的网络传输协议,可在不安全的网络中为网络服务提供安全的传输环境。
SSH通过在网络中创建安全隧道来实现SSH客户端与服务器之间的连接。SSH最常见的用途是远程登录系统,人们通常利用SSH来传输
命令行界面和远程执行命令。

SCP 代表安全复制协议,它对 Linux 系统之间的文件传输进行加密。SCP 是一个命令行工具,可用于跨 Linux 系统安全地复制或传输文件和目录。
SCP 在 SSH(安全外壳)连接上使用加密,这确保即使数据被截获,它仍然受到保护。

## SSH 使用

ssh [ip] -l [username] -p [port]
或者
ssh [user]@[ip] -p [port]
ssh [username]@[ip]:[port]
如:
ssh [root@jobs8.cn] -p 22
ssh [root@jobs8.cn]:22

### 连接保活

ClientAliveInterval 60  # server 每隔 60 秒发送一次请求给 client,然后 client 响应,从而保持连接
ClientAliveCountMax 3   # server 发出请求后,客户端没有响应得次数达到 3 就自动断开连接,正常情况下 client 不会不响应
如:
ssh -o ServerAliveInterval=60 [root@jobs8.cn] -p 22

## SCP 使用

用法和linux 上 cp 命令类似,只不过如果目标文件在远程服务器上需要用[username]@[ip]指定服务器

1. 上传
scp -r [filepath] [username]@[ip]:[directory]
如:
scp -r ./test.txt <root@jobs8.cn>:/tmp
2. 下载
scp -r [username]@[ip]:[filepath] [directory]
如:
scp -r <root@jobs8.cn>:/tmp/test.txt ./
3. 指定端口 -P [port] (是大写的P)如:
scp -P 2222 -r ./test.txt <root@jobs8.cn>:/tmp
注:如果不指定端口,则默认端口是 22
