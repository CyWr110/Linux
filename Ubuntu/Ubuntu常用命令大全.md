一、文件/文件夹管理


ls 列出当前目录文件（不包括隐含文件）
ls -a 列出当前目录文件（包括隐含文件）
ls -l 列出当前目录下文件的详细信息

cd .. 回当前目录的上一级目录
cd - 回上一次所在的目录
cd ~ 或 cd 回当前用户的宿主目录
mkdir 目录名 创建一个目录
rmdir 空目录名 删除一个空目录
rm 文件名 文件名 删除一个文件或多个文件
rm -rf 非空目录名 删除一个非空目录下的一切

mv 路经/文件 /经/文件移动相对路经下的文件到绝对路经下
mv 文件名 新名称 在当前目录下改名
find 路经 -name “字符串” 查找路经所在范围内满足字符串匹配的文件和目录

二、系统管理

fdisk fdisk -l 查看系统分区信息
fdisk fdisk /dev/sdb 为一块新的SCSI硬盘进行分区
chown chown root /home 把/home的属主改成root用户
chgrp chgrp root /home 把/home的属组改成root组

Useradd 创建一个新的用户
Groupadd 组名 创建一个新的组
Passwd 用户名 为用户创建密码
Passwd -d用户名 删除用户密码也能登陆
Passwd -S用户名 查询账号密码
Usermod -l 新用户名 老用户名 为用户改名
Userdel–r 用户名 删除用户一切

service [servicename] start/stop/restart 系统服务控制操作
/etc/init.d/[servicename] start/stop/restart 系统服务控制操作

uname -a 查看内核版本
cat /etc/issue 查看ubuntu版本
lsusb 查看usb设备
sudo ethtool eth0 查看网卡状态
cat /proc/cpuinfo 查看cpu信息
lshw 查看当前硬件信息
sudo fdisk -l 查看磁盘信息
df -h 查看硬盘剩余空间
free -m 查看当前的内存使用情况
ps -A 查看当前有哪些进程
kill 进程号(就是ps -A中的第一列的数字)或者 killall 进程名( 杀死一个进程)
kill -9 进程号 强制杀死一个进程

reboot Init 6 重启LINUX系统
Halt Init 0 Shutdown –h now 关闭LINUX系统

三、打包/解压

tar -c 创建包 –x 释放包 -v 显示命令过程 –z 代表压缩包
tar –cvf benet.tar /home/benet 把/home/benet目录打包
tar –zcvf benet.tar.gz /mnt 把目录打包并压缩
tar –zxvf benet.tar.gz 压缩包的文件解压恢复
tar –jxvf benet.tar.bz2 解压缩

四、make编译

make 编译
make install 安装编译好的源码包

五、apt命令

apt-cache search package 搜索包
apt-cache show package 获取包的相关信息，如说明、大小、版本等
sudo apt-get install package 安装包
sudo apt-get install package - - reinstall 重新安装包
sudo apt-get -f install 修复安装”-f = –fix-missing”
sudo apt-get remove package 删除包
sudo apt-get remove package - - purge 删除包，包括删除配置文件等
sudo apt-get update 更新源
sudo apt-get upgrade 更新已安装的包
sudo apt-get dist-upgrade 升级系统
sudo apt-get dselect-upgrade 使用 dselect 升级
apt-cache depends package 了解使用依赖
apt-cache rdepends package 是查看该包被哪些包依赖
sudo apt-get build-dep package 安装相关的编译环境
apt-get source package 下载该包的源代码
sudo apt-get clean && sudo apt-get autoclean 清理无用的包
sudo apt-get check 检查是否有损坏的依赖
sudo apt-get clean 清理所有软件缓存（即缓存在/var/cache/apt/archives目录里的deb包）

查看软件xxx安装内容
#dpkg -L xxx

查找软件
#apt-cache search 正则表达式
查找文件属于哪个包
#dpkg -S filename apt-file search filename

查询软件xxx依赖哪些包
#apt-cache depends xxx

查询软件xxx被哪些包依赖
#apt-cache rdepends xxx

增加一个光盘源
#sudo apt-cdrom add

系统升级
#sudo apt-get update
#sudo apt-get upgrade
#sudo apt-get dist-upgrade

清除所以删除包的残余配置文件
#dpkg -l |grep ^rc|awk ‘{print $2}’ |tr ["\n"] [" “]|sudo xargs dpkg -P -

编译时缺少h文件的自动处理
#sudo auto-apt run ./configure

查看安装软件时下载包的临时存放目录
#ls /var/cache/apt/archives

备份当前系统安装的所有包的列表
#dpkg –get-selections | grep -v deinstall > ~/somefile

从上面备份的安装包的列表文件恢复所有包
#dpkg –set-selections < ~/somefile sudo dselect

清理旧版本的软件缓存
#sudo apt-get autoclean

清理所有软件缓存
#sudo apt-get clean

删除系统不再使用的孤立软件
#sudo apt-get autoremove

查看包在服务器上面的地址
#apt-get -qq –print-uris install ssh | cut -d\’ -f2

系统
查看内核
#uname -a

查看Ubuntu版本
#cat /etc/issue

查看内核加载的模块
#lsmod

查看PCI设备
#lspci

查看USB设备
#lsusb

查看网卡状态
#sudo ethtool eth0

查看CPU信息
#cat /proc/cpuinfo

显示当前硬件信息
#lshw

硬盘
查看硬盘的分区
#sudo fdisk -l

查看IDE硬盘信息
#sudo hdparm -i /dev/hda

查看STAT硬盘信息
#sudo hdparm -I /dev/sda
或
#sudo apt-get install blktool
#sudo blktool /dev/sda id

查看硬盘剩余空间
#df -h
#df -H

查看目录占用空间
#du -hs 目录名

优盘没法卸载
#sync fuser -km /media/usbdisk

内存
查看当前的内存使用情况
#free -m

进程
查看当前有哪些进程
#ps -A
中止一个进程
#kill 进程号(就是ps -A中的第一列的数字) 或者 killall 进程名

强制中止一个进程(在上面进程中止不成功的时候使用)
#kill -9 进程号 或者 killall -9 进程名

图形方式中止一个程序
#xkill 出现骷髅标志的鼠标，点击需要中止的程序即可

查看当前进程的实时状况
#top

查看进程打开的文件
#lsof -p

ADSL 配置 ADSL
#sudo pppoeconf

ADSL手工拨号
#sudo pon dsl-provider

激活 ADSL
#sudo /etc/ppp/pppoe_on_boot

断开 ADSL
#sudo poff

查看拨号日志
#sudo plog

如何设置动态域名
#首先去http://www.3322.org申请一个动态域名
#然后修改 /etc/ppp/ip-up 增加拨号时更新域名指令 sudo vim /etc/ppp/ip-up
#在最后增加如下行 w3m -no-cookie -dump

网络
根据IP查网卡地址
#arping IP地址

查看当前IP地址
#ifconfig eth0 |awk ‘/inet/ {split($2,x,":");print x[2]}’

查看当前外网的IP地址
#w3m -no-cookie -dumpwww.edu.cn|grep-o‘[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}’
#w3m -no-cookie -dumpwww.xju.edu.cn|grep-o’[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}’
#w3m -no-cookie -dump ip.loveroot.com|grep -o’[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}’

查看当前监听80端口的程序
#lsof -i :80

查看当前网卡的物理地址
#arp -a | awk ‘{print $4}’ ifconfig eth0 | head -1 | awk ‘{print $5}’

立即让网络支持nat
#sudo echo 1 > /proc/sys/net/ipv4/ip_forward
#sudo iptables -t nat -I POSTROUTING -j MASQUERADE

查看路由信息
#netstat -rn sudo route -n

手工增加删除一条路由
#sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 172.16.0.1
#sudo route del -net 192.168.0.0 netmask 255.255.255.0 gw 172.16.0.1

修改网卡MAC地址的方法
#sudo ifconfig eth0 down 关闭网卡
#sudo ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE 然后改地址
#sudo ifconfig eth0 up 然后启动网卡

统计当前IP连接的个数
#netstat -na|grep ESTABLISHED|awk ‘{print $5}’|awk -F: ‘{print $1}’|sort|uniq -c|sort -r -n
#netstat -na|grep SYN|awk ‘{print $5}’|awk -F: ‘{print $1}’|sort|uniq -c|sort -r -n

统计当前20000个IP包中大于100个IP包的IP地址
#tcpdump -tnn -c 20000 -i eth0 | awk -F “." ‘{print $1″."$2″."$3″."$4}’ | sort | uniq -c | sort -nr | awk ‘ $1 > 100 ‘

屏蔽IPV6
#echo “blacklist ipv6″ | sudo tee /etc/modprobe.d/blacklist-ipv6

服务
添加一个服务
#sudo update-rc.d 服务名 defaults 99

删除一个服务
#sudo update-rc.d 服务名 remove

临时重启一个服务
#/etc/init.d/服务名 restart

临时关闭一个服务
#/etc/init.d/服务名 stop

临时启动一个服务
#/etc/init.d/服务名 start

设置
配置默认Java使用哪个
#sudo update-alternatives –config java

修改用户资料
#sudo chfn userid

给apt设置代理
#export http_proxy=http://xx.xx.xx.xx:xxx

修改系统登录信息
#sudo vim /etc/motd

中文
转换文件名由GBK为UTF8
#sudo apt-get install convmv convmv -r -f cp936 -t utf8 –notest –nosmart *

批量转换src目录下的所有文件内容由GBK到UTF8
#find src -type d -exec mkdir -p utf8/{} \; find src -type f -exec iconv -f GBK -t UTF-8 {} -o utf8/{} \; mv utf8/* src rm -fr utf8

转换文件内容由GBK到UTF8
#iconv -f gbk -t utf8 $i > newfile

转换 mp3 标签编码
#sudo apt-get install python-mutagen find . -iname “*.mp3" -execdir mid3iconv -e GBK {} \;

控制台下显示中文
#sudo apt-get install zhcon 使用时，输入zhcon即可

文件
快速查找某个文件
#whereis filename
#find 目录 -name 文件名

查看文件类型
#file filename

显示xxx文件倒数6行的内容
#tail -n 6 xxx

让tail不停地读地最新的内容
#tail -n 10 -f /var/log/apache2/access.log

查看文件中间的第五行（含）到第10行（含）的内容
#sed -n ‘5,10p’ /var/log/apache2/access.log

查找包含xxx字符串的文件
#grep -l -r xxx .

全盘搜索文件(桌面可视化)
gnome-search-tool

查找关于xxx的命令
#apropos xxx man -k xxx

通过ssh传输文件
#scp -rp /path/filenameusername@remoteIP:/path
#将本地文件拷贝到服务器上
#scp -rpusername@remoteIP:/path/filename/path
#将远程文件从服务器下载到本地

查看某个文件被哪些应用程序读写
#lsof 文件名

把所有文件的后辍由rm改为rmvb
#rename ’s/.rm$/.rmvb/’ *

把所有文件名中的大写改为小写
#rename ‘tr/A-Z/a-z/’ *

删除特殊文件名的文件，如文件名：–help.txt
#rm — –help.txt 或者 rm ./–help.txt

查看当前目录的子目录
#ls -d */. 或 echo */.

将当前目录下最近30天访问过的文件移动到上级back目录
#find . -type f -atime -30 -exec mv {} ../back \;

将当前目录下最近2小时到8小时之内的文件显示出来
#find . -mmin +120 -mmin -480 -exec more {} \;

删除修改时间在30天之前的所有文件
#find . -type f -mtime +30 -mtime -3600 -exec rm {} \;

查找guest用户的以avi或者rm结尾的文件并删除掉
#find . -name ‘*.avi’ -o -name ‘*.rm’ -user ‘guest’ -exec rm {} \;

查找的不以java和xml结尾,并7天没有使用的文件删除掉
#find . ! -name *.java ! -name ‘*.xml’ -atime +7 -exec rm {} \;

统计当前文件个数
#ls /usr/bin|wc -w

统计当前目录个数
#ls -l /usr/bin|grep ^d|wc -l

显示当前目录下2006-01-01的文件名
#ls -l |grep 2006-01-01 |awk ‘{print $8}’

FTP
上传下载文件工具-filezilla
#sudo apt-get install filezilla

filezilla无法列出中文目录？
站点->字符集->自定义->输入：GBK

本地中文界面
1）下载filezilla中文包到本地目录，如~/
2）#unrar x Filezilla3_zhCN.rar
3) 如果你没有unrar的话，请先安装rar和unrar
#sudo apt-get install rar unrar
#sudo ln -f /usr/bin/rar /usr/bin/unrar
4）先备份原来的语言包,再安装；实际就是拷贝一个语言包。
#sudo cp /usr/share/locale/zh_CN/filezilla.mo /usr/share/locale/zh_CN/filezilla.mo.bak
#sudo cp ~/locale/zh_CN/filezilla.mo /usr/share/locale/zh_CN/filezilla.mo
5）重启filezilla,即可！

解压缩
解压缩 xxx.tar.gz
#tar -zxvf xxx.tar.gz

解压缩 xxx.tar.bz2
#tar -jxvf xxx.tar.bz2

压缩aaa bbb目录为xxx.tar.gz
#tar -zcvf xxx.tar.gz aaa bbb

压缩aaa bbb目录为xxx.tar.bz2
#tar -jcvf xxx.tar.bz2 aaa bbb

解压缩 RAR 文件
1) 先安装
#sudo apt-get install rar unrar
#sudo ln -f /usr/bin/rar /usr/bin/unrar
2) 解压
#unrar x aaaa.rar

Nautilus
显示隐藏文件
Ctrl+h

显示地址栏
Ctrl+l

特殊 URI 地址
* computer:/// - 全部挂载的设备和网络
* network:/// - 浏览可用的网络
* burn:/// - 一个刻录 CDs/DVDs 的数据虚拟目录
* smb:/// - 可用的 windows/samba 网络资源
* x-nautilus-desktop:/// - 桌面项目和图标
*file:///- 本地文件
* trash:/// - 本地回收站目录
* ftp:// - FTP 文件夹
* ssh:// - SSH 文件夹
* fonts:/// - 字体文件夹，可将字体文件拖到此处以完成安装
* themes:/// - 系统主题文件夹

查看已安装字体
在nautilus的地址栏里输入"fonts:///“，就可以查看本机所有的fonts

程序
详细显示程序的运行信息
#strace -f -F -o outfile

日期和时间

设置日期
#date -s mm/dd/yy

设置时间
#date -s HH:MM

将时间写入CMOS
#hwclock –systohc

读取CMOS时间
#hwclock –hctosys

从服务器上同步时间
#sudo ntpdate time.nist.gov
#sudo ntpdate time.windows.com

控制台

不同控制台间切换
Ctrl + ALT + ← Ctrl + ALT + →

指定控制台切换
Ctrl + ALT + Fn(n:1~7)

控制台下滚屏
SHIFT + pageUp/pageDown

控制台抓图
#setterm -dump n(n:1~7)

数据库
mysql的数据库存放在地方
#/var/lib/mysql

从mysql中导出和导入数据
#mysqldump 数据库名 > 文件名 #导出数据库
#mysqladmin create 数据库名 #建立数据库
#mysql 数据库名 < 文件名 #导入数据库

忘了mysql的root口令怎么办
#sudo /etc/init.d/mysql stop
#sudo mysqld_safe –skip-grant-tables
#sudo mysqladmin -u user password ‘newpassword"
#sudo mysqladmin flush-privileges

修改mysql的root口令
#sudo mysqladmin -uroot -p password ‘你的新密码’

其它
下载网站文档
#wget -r -p -np -khttp://www.21cn.com
· r：在本机建立服务器端目录结构；
· -p: 下载显示HTML文件的所有图片；
· -np：只下载目标站点指定目录及其子目录的内容；
· -k: 转换非相对链接为相对链接。

如何删除Totem电影播放机的播放历史记录
#rm ~/.recently-used

如何更换gnome程序的快捷键
点击菜单，鼠标停留在某条菜单上，键盘输入任意你所需要的键，可以是组合键，会立即生效； 如果要清除该快捷键，请使用backspace

vim 如何显示彩色字符
#sudo cp /usr/share/vim/vimcurrent/vimrc_example.vim /usr/share/vim/vimrc

如何在命令行删除在会话设置的启动程序
#cd ~/.config/autostart rm 需要删除启动程序

如何提高wine的反应速度
#sudo sed -ie ‘/GBK/,/^}/d’ /usr/share/X11/locale/zh_CN.UTF-8/XLC_LOCALE

#chgrp
[语法]: chgrp [-R] 文件组 文件…
[说明]： 文件的GID表示文件的文件组，文件组可用数字表示， 也可用一个有效的组名表示，此命令改变一个文件的GID，可参看chown。
-R 递归地改变所有子目录下所有文件的存取模式
[例子]:
＃chgrp group file 将文件 file 的文件组改为 group

#chmod
[语法]: chmod [-R] 模式 文件…
或 chmod [ugoa] {+|-|=} [rwxst] 文件…
[说明]: 改变文件的存取模式，存取模式可表示为数字或符号串，例如：
＃chmod nnnn file ， n为0-7的数字，意义如下:
4000 运行时可改变UID
2000 运行时可改变GID
1000 置粘着位
0400 文件主可读
0200 文件主可写
0100 文件主可执行
0040 同组用户可读
0020 同组用户可写
0010 同组用户可执行
0004 其他用户可读
0002 其他用户可写
0001 其他用户可执行
nnnn 就是上列数字相加得到的，例如 chmod 0777 file 是指将文件 file 存取权限置为所有用户可读可写可执行。
-R 递归地改变所有子目录下所有文件的存取模式
u 文件主
g 同组用户
o 其他用户
a 所有用户
+ 增加后列权限
- 取消后列权限
= 置成后列权限
r 可读
w 可写
x 可执行
s 运行时可置UID
t 运行时可置GID
[例子]:
＃chmod 0666 file1 file2 将文件 file1 及 file2 置为所有用户可读可写
＃chmod u+x file 对文件 file 增加文件主可执行权限
＃chmod o-rwx 对文件file 取消其他用户的所有权限

#chown
[语法]: chown [-R] 文件主 文件…
[说明]: 文件的UID表示文件的文件主，文件主可用数字表示， 也可用一个有效的用户名表示，此命令改变一个文件的UID，仅当此文件的文件主或超级用户可使用。
-R 递归地改变所有子目录下所有文件的存取模式
[例子]:
#chown mary file 将文件 file 的文件主改为 mary
#chown 150 file 将文件 file 的UID改为150

Ubuntu命令行下修改网络配置
以eth0为例
1. 以DHCP方式配置网卡
编辑文件/etc/network/interfaces:
#sudo vi /etc/network/interfaces
并用下面的行来替换有关eth0的行:
# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp
用下面的命令使网络设置生效:
#sudo /etc/init.d/networking restart
当然,也可以在命令行下直接输入下面的命令来获取地址
#sudo dhclient eth0

2. 为网卡配置静态IP地址
编辑文件/etc/network/interfaces:
#sudo vi /etc/network/interfaces
并用下面的行来替换有关eth0的行:
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
将上面的ip地址等信息换成你自己就可以了.

用下面的命令使网络设置生效:
#sudo /etc/init.d/networking restart

3. 设定第二个IP地址(虚拟IP地址)
编辑文件/etc/network/interfaces:
#sudo vi /etc/network/interfaces
在该文件中添加如下的行:
auto eth0:1
iface eth0:1 inet static
address 192.168.1.60
netmask 255.255.255.0
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x
根据你的情况填上所有诸如address,netmask,network,broadcast和gateways等信息.
用下面的命令使网络设置生效:
#sudo /etc/init.d/networking restart

4. 设置主机名称(hostname)
使用下面的命令来查看当前主机的主机名称:
#sudo /bin/hostname
使用下面的命令来设置当前主机的主机名称:
#sudo /bin/hostname newname
系统启动时,它会从/etc/hostname来读取主机的名称.

5. 配置DNS
首先,你可以在/etc/hosts中加入一些主机名称和这些主机名称对应的IP地址,这是简单使用本机的静态查询.
要访问DNS 服务器来进行查询,需要设置/etc/resolv.conf文件.
假设DNS服务器的IP地址是192.168.3.2, 那么/etc/resolv.conf文件的内容应为:
search test.com
nameserver 192.168.3.2

安装AMP服务
如果采用Ubuntu Server CD开始安装时，可以选择安装，这系统会自动装上apache2,php5和mysql5。下面主要说明一下如果不是安装的Ubuntu server时的安装方法。
用命令在Ubuntu下架设Lamp其实很简单，用一条命令就完成。在终端输入以下命令：
#sudo apt-get install apache2 mysql-server php5 php5-mysql php5-gd #phpmyadmin
装好后，mysql管理员是root，无密码，通过http://localhost/phpmyadmin就可以访问mysql了

修改 MySql 密码
终端下输入：
#mysql -u root
#mysql> GRANT ALL PRIVILEGES ON *.* TO root@localhost IDENTIFIED BY “123456″;
’123456‘是root的密码，可以自由设置，但最好是设个安全点的。
#mysql> quit; 退出mysql

apache2的操作命令
启动：#sudo /etc/init.d/apache2 start
重启：#sudo /etc/init.d/apache2 restart
关闭：#sudo /etc/init.d/apache2 stop
apache2的默认主目录：/var/www/

Ubuntu 7.10 更换软件源、更新系统
网通建议用台湾的源，电信就用cn99
在终端输入: #sudo gedit /etc/apt/sources.list

# Ubuntu.cn99.com 更新服务器（江苏省常州市电信，推荐电信用户使用。）
deb http://ubuntu.cn99.com/ubuntu/ gutsy main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-updates main restricted universe multiverse
# mirror.rootguide.org更新服务器 (上海市 电信):
deb http://mirror.rootguide.org/ubuntu/ gutsy main restricted universe multiverse
deb-src http://mirror.rootguide.org/ubuntu/ gutsy main restricted universe multiverse
deb http://mirror.rootguide.org/ubuntu/ gutsy-updates main restricted universe multiverse
# Mirror.lupaworld.com 更新服务器（浙江省杭州市电信，亚洲地区官方更新服务器）
deb http://cn.archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
# ubuntu.cnsite.org 更新服务器（福建省福州市 电信）
deb http://ubuntu.cnsite.org/ubuntu/ gutsy main restricted universe multiverse
deb-src http://ubuntu.cnsite.org/ubuntu/ gutsy main restricted universe multiverse
deb http://ubuntu.cnsite.org/ubuntu/ gutsy-updates main restricted universe multiverse
#清华大学 更新服务器（教育网，推荐校园网和网通用户使用）
deb http://mirror9.net9.org/ubuntu/ gutsy main multiverse restricted universe
deb http://mirror9.net9.org/ubuntu/ gutsy-backports main multiverse restricted universe
deb http://mirror9.net9.org/ubuntu/ gutsy-proposed main multiverse restricted universe
将里面乱七八糟的东西删了，将你复制的源列表粘贴到里面，保存退出。
在终端输入
#sudo apt-get update
#sudu apt-get upgrade

这样便更新以及升级了系统。

桌面汉化：
System>Language Support>Chinese选项勾打上。

安装解码器、flashplayer、java虚拟机、微软字体
这是ubuntu推出的一个新软件包，将一次性将上面几个东东自动装好
在终端输入
#sudo apt-get install ubuntu-restricted-extras

FireFox 中安装 FlashPlayer 插件
先下载插件: install_flash_player_9_linux.tar.gz
#tar -zxf install_flash_player_9_linux.tar.gz
#./flashplayer-installer

回答(y/n/q)? n/q
#sudo cp libflashplayer.so /usr/lib/firefox/plugins
启动 firefox 即可！

安装媒体播放器
安装的是mplayer
终端输入：#sudo apt-get install mplayer mozilla-mplayer totem-xine libxine-extracodecs

另外需要一个w32codecs文件，是用来支持那些私有媒体格式的解码器，源里已经没有w32codecs了，我们可以从这里下载那个后缀为.deb的安装
http://www.debian-multimedia.org/pool/main/w/w32codecs/

mplayer调试(视频、字幕)
启动mplayer,右键－>Preferences－>Video
Available drivers选择xv
然后进入Font标签 Font里选择一个中文字体，Encoding里设置为Simplified Chinese charset (CP936)

安装下载工具（多线程下载、BT下载、电驴）
还是终端输入：#sudo apt-get install d4x amule azureus
即可。
或者把 beryl-manager添加到启动项内

字体更换
我推荐大家使用文泉驿字体，在
http://wqy.sourceforge.net
下载deb包安装
在“系统“－>"首选项“－>"字体“中调整字体

apt下载的deb包清理
在使用完apt后，系统下载的deb包会留存在硬盘里，我们可以把它们删除，释放硬盘空间。
终端输入：#sudo apt-get clean

安装rar压缩、解压工具
终端输入：#sudo apt-get install rar unrar

启用root（最高权限）帐户
终端输入：#sudo passwd root
输入你希望的root用户的密码

安装QQ
终端输入：#sudo apt-get install eva
便可安装eva了，如果你是使用scim(选择中文语言支持的自动安装的就是scim)，为了可以在eva里面输入文字，要在终端输入：sudo apt-get install scim-qtimm
系统会安装支持QT的scim插件，这样你就可以使用eva聊qq了。

显卡驱动安装
进入“系统"－>“系统管理"－>“受限驱动管理器"
找到你的显卡，把那个框点成对号，会提示你安装显卡驱动，然后按照提示一步一步安装完毕，重启即可。

beryl的安装
你的系统在安装完毕之后就已经有了一个内置的桌面效果软件（能实现简单的桌面特效，包括3D立方体），使用方法是（必须将显卡驱动装好）进入“系统"“首选项"“桌面效果"，点击“启用桌面效果"，如果你需要使用3D立方体桌面，那么选中“立方体上的工作区"即可。
如果你对这个简单的桌面特效工具不太满意，想追求更华丽的桌面，那么安装beryl仍然是个很好的选择。如今安装beryl不会像以前一样麻烦了，feisty的源里已经有了beryl的软件包，我们只需要在终端里输入：
#sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
安装完毕即可了。
启动方法：“应用程序"－>"系统工具"－>"Beryl Manager"
或者直接在终端输入：#beryl-manager

如何设定/改变/启用 root 使用者的密码?
#sudo passwd root

为了启用 root 帐号 (也就是 设置一个口令) 使用:
#sudo passwd root

当你使用完毕后屏蔽 root 帐号 使用:
#sudo passwd -l root
这个将锁住 root 帐号.

如何在终端机模式下切换到 root 身份?
#sudo -s -H
Password: <在这注明您的密码>

安装VNC server
第一步, 获取安装文件
#sudo apt-get install vnc4server
第二步, 修改VNC Password, 6-8位
#vncpasswd
Password: ******
Verify:*****
第三步, 修改配置
系统->首选项->远程桌面
选择->请求用户输入此密码->输入至少6位密码
第四步, 启动VNC server
#vncserver
第五步，通过客户端连接
#vncviewer 192.168.0.1

安装MS字体
#sudo apt-get install msttcorefonts

vim配置
1) 首先安装 vim 完整版本
#sudo apt-get install vim-full

2) vim中文在线帮助
a. 先下载文档 vimcdoc-1.5.0.tar.gz
b. 解压, 执行./vimcdoc.sh, vi里面, 执行:help, 就都是中文的了.

3) 启用本地配置 VIM version 7.1 (说明文档)
#cp etc/vim/vimrc ~/.vimrc
#vim ~/.vimrc

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 一般设定
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 设定默认解码
set fenc=utf-8
set fencs=utf-8,usc-bom,euc-jp,gb18030,gbk,gb2312,cp936
" 不要使用vi的键盘模式，而是vim自己的
set nocompatible

" history文件中需要记录的行数
set history=100

" 在处理未保存或只读文件的时候，弹出确认
set confirm

" 与windows共享剪贴板
set clipboard+=unnamed

" 侦测文件类型
filetype on

" 载入文件类型插件
filetype plugin on

" 为特定文件类型载入相关缩进文件
filetype indent on

" 保存全局变量
set viminfo+=!

" 带有如下符号的单词不要被换行分割
set iskeyword+=_,$,@,%,#,-

" 语法高亮
syntax on

" 高亮字符，让其不受100列限制
:highlight OverLength ctermbg=red ctermfg=white guibg=red guifg=white
:match OverLength ‘\%101v.*’

" 状态行颜色
highlight StatusLine guifg=SlateBlue guibg=Yellow
highlight StatusLineNC guifg=Gray guibg=White

“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 文件设置
“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 不要备份文件（根据自己需要取舍）
set nobackup

" 不要生成swap文件，当buffer被丢弃的时候隐藏它
setlocal noswapfile
set bufhidden=hide

" 字符间插入的像素行数目
set linespace=0

" 增强模式中的命令行自动完成操作
set wildmenu

" 在状态行上显示光标所在位置的行号和列号
set ruler
set rulerformat=%20(%2*%<%f%=\ %m%r\ %3l\ %c\ %p%%%)

" 命令行（在状态行下）的高度，默认为1，这里是2
set cmdheight=2

" 使回格键（backspace）正常处理indent, eol, start等
set backspace=2

" 允许backspace和光标键跨越行边界
set whichwrap+=<,>,h,l

" 可以在buffer的任何地方使用鼠标（类似office中在工作区双击鼠标定位）
set mouse=a
set selection=exclusive
set selectmode=mouse,key

" 启动的时候不显示那个援助索马里儿童的提示
set shortmess=atI

" 通过使用: commands命令，告诉我们文件的哪一行被改变过
set report=0

" 不让vim发出讨厌的滴滴声
set noerrorbells

" 在被分割的窗口间显示空白，便于阅读
set fillchars=vert:\ ,stl:\ ,stlnc:\

“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 搜索和匹配
“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 高亮显示匹配的括号
set showmatch

" 匹配括号高亮的时间（单位是十分之一秒）
set matchtime=5

" 在搜索的时候忽略大小写
set ignorecase

" 不要高亮被搜索的句子（phrases）
set nohlsearch

" 在搜索时，输入的词句的逐字符高亮（类似firefox的搜索）
set incsearch

" 输入:set list命令是应该显示些啥？
set listchars=tab:\|\ ,trail:.,extends:>,precedes:<,eol:$

" 光标移动到buffer的顶部和底部时保持3行距离
set scrolloff=3

" 不要闪烁
set novisualbell

" 我的状态行显示的内容（包括文件类型和解码）
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [POS=%l,%v][%p%%]\ %{strftime(\"%d/%m/%y\ -\ %H:%M\")}

" 总是显示状态行
set laststatus=2

“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 文本格式和排版
“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 自动格式化
set formatoptions=tcrqn

" 继承前一行的缩进方式，特别适用于多行注释
set autoindent

" 为C程序提供自动缩进
set smartindent

" 使用C样式的缩进
set cindent

" 制表符为4
set tabstop=4

" 统一缩进为4
set softtabstop=4
set shiftwidth=4

" 不要用空格代替制表符
set noexpandtab

" 不要换行
set nowrap

" 在行和段开始处使用制表符
set smarttab

“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" CTags的设定
“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 按照名称排序
let Tlist_Sort_Type = “name"

" 在右侧显示窗口
let Tlist_Use_Right_Window = 1

" 压缩方式
let Tlist_Compart_Format = 1

" 如果只有一个buffer，kill窗口也kill掉buffer
let Tlist_Exist_OnlyWindow = 1

" 不要关闭其他文件的tags
let Tlist_File_Fold_Auto_Close = 0

" 不要显示折叠树
let Tlist_Enable_Fold_Column = 0

“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Autocommands
“""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 只在下列文件类型被侦测到的时候显示行号，普通文本文件不显示

if has("autocmd")
autocmd FileType xml,html,c,cs,java,perl,shell,bash,cpp,python,vim,php,ruby set number
autocmd FileType xml,html vmap
