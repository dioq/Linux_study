# 常用命令

## apt 使用

列出已安装软件包
apt list --installed

apt 删除已经安装的软件包：
apt-get purge / apt-get --purge remove          删除已安装包(不保留配置文件)。如软件包a,依赖软件包b,则执行该命令会删除a,而且不保留配置文件
apt-get autoremove                              删除为了满足依赖而安装的,但现在不再需要的软件包（包括已安装包）,保留配置文件。
apt-get remove                                  删除已安装的软件包（保留配置文件）,不会删除依赖软件包,且保留配置文件。
apt-get autoclean                               APT的底层包是dpkg, 而dpkg 安装Package时, 会将 *.deb 放在 /var/cache/apt/archives/中,apt-get autoclean 只会删除 /var/cache/apt/archives/ 已经过期的deb。
apt-get clean                                   使用 apt-get clean 会将 /var/cache/apt/archives/ 的 所有 deb 删掉,可以理解为 rm /var/cache/apt/archives/*.deb

## 通过deb包安装软件

dpkg -i package_file.deb
卸载:
dpkg -r package_name
注意,卸载时候是package_file.deb对应的package name
若不知道package name,可以通过
dpkg -l查找,若要查找对应的package,可以加通配符,如查找包含fox的package
dpkg -l *fox*即可
查到以后,可以运行
dpkg -r package_name卸载
dpkg --purge to remove package_name

## cli 打开文件夹

nautilus [dir path]
