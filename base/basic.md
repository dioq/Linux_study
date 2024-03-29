# 基础命令

## 运行程序

后台运行
./xxx &
退出 terminal 的时候继续运行进程,则需要使用nohup忽略hangup信号
nohup ./test.sh &

## ls 显示文件信息

options:
-l 显示属性
-a 显示信息
-S  sort by file size   (默认由大到小)
-t  sort by create time (默认由大到小)
-r  是reverse的简写,表示反转

如:
ls ./test      # 显示 ./test 目录下可见文件名
ls ./test -l  # 显示 ./test 目录下可见文件名和属性
ls ./test -la     # 显示 ./test 目录下所有可见文件名和属性

lsof                # (list open files) 查看进程打开的文件
options:
-a 指示其它选项之间为与的关系
-c <进程名> 输出指定进程所打开的文件
-d <文件描述符> 列出占用该文件号的进程
+d <目录>  输出目录及目录下被打开的文件和目录(不递归)
+D <目录>  递归输出及目录下被打开的文件和目录
-i <条件>  输出符合条件与网络相关的文件
-n 不解析主机名
-p <进程号> 输出指定 PID 的进程所打开的文件
-P 不解析端口号
-t 只输出 PID
-u 输出指定用户打开的文件
-U 输出打开的 UNIX domain socket 文件
-h 显示帮助信息
-v 显示版本信息

## grep 过滤

ls ./test/ | grep *.txt         # 过虑 ./test 目录下 后缀为txt的文件

## wget下载

-c      支持断点续传
wget -c <https://1.na.dl.wireshark.org/win64/Wireshark-win64-3.2.4.exe>

## 软件链接

创建软链接
ln  -s  [源文件或目录]  [目标文件或目录]
例如:
当前路径创建test 引向/var/www/test 文件夹
ln -s  /var/www/test  test
创建/var/test 引向/var/www/test 文件夹
ln -s  /var/www/test   /var/test

删除软链接
和删除普通的文件是一眼的,删除都是使用rm来进行操作
rm -rf 软链接名称
例如:
删除test
rm -rf test
