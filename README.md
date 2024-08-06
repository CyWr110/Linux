#命令 #常用命令 #dcoker #snell #节点搭建 #Linux命令 #节点 #Linux 


* root权限：
```
sudo -i
```

* vps系统更新：
```
apt update
```

* 科技lion脚本：
```
curl -sS -O https://kejilion.pro/kejilion.sh && chmod +x kejilion.sh && ./kejilion.sh
```

* 通过yum安装wegt
```
yum install wget
```

* warp脚本：
```
wget -N https://gitlab.com/fscarmen/warp/-/raw/main/menu.sh && bash menu.sh [option] [lisence/url/token]
```
再次启动：
```
warp [option] [lisence]
```

* 解锁测试脚本：
```
bash <(curl -L -s media.ispvps.com)
```

* xui脚本：
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```
```
bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh) 0.3.4.4
```

* Docker 官方一键安装
```
curl -fsSL https://get.docker.com | bash -s docker
```

* 一键安装 Telegram 人形 bot
```
sudo bash -c "$(curl -sL https://raw.githubusercontent.com/durianice/pgp-install/main/docker-install.sh)"
```

* 一键 Snell V4
```
wget -O snell.sh --no-check-certificate https://git.io/Snell.sh && chmod +x snell.sh && ./snell.sh
```

* 一键 SS
```
wget -O ss-rust.sh --no-check-certificate https://raw.githubusercontent.com/xOS/Shadowsocks-Rust/master/ss-rust.sh && chmod +x ss-rust.sh && ./ss-rust.sh
```

* 一键 hy2 (第一种Surge可以直接使用)
```
bash <(curl -Ls https://raw.githubusercontent.com/passeway/Hysteria/main/Hysteria2.sh)
```
```
wget -N --no-check-certificate https://raw.githubusercontent.com/Misaka-blog/hysteria-install/main/hy2/hysteria.sh && bash hysteria.sh
```

* 测试回程路由
```
bash <(curl -Ls https://raw.githubusercontent.com/sjlleo/nexttrace/main/nt_install.sh)
```

* 一键DD脚本（ -d 后面为Debian版本号，-v 后面为64位/32位，可根据需求进行替换。）秋水逸冰改自萌咖
```
bash <(wget --no-check-certificate -qO- 'qiu.sh/dd') -d 11 -v 64 -p <自定义密码> -port <自定义端口>
```

* IP质量体检脚本
默认双栈检测：
```
bash <(curl -Ls IP.Check.Place)
```
只检测IPv4结果：
```
bash <(curl -Ls IP.Check.Place) -4
```
只检测IPv6结果：
```
bash <(curl -Ls IP.Check.Place) -6
```

* hy2脚本：
```
wget -N --no-check-certificate https://raw.githubusercontent.com/Misaka-blog/hysteria-install/main/hy2/hysteria.sh && bash hysteria.sh
```

* argox节点脚本：
```
bash <(wget -qO- https://raw.githubusercontent.com/fscarmen/argox/main/argox.sh)
```

* 脚本合集：
```
curl -fsSL https://raw.githubusercontent.com/eooce/ssh_tool/main/ssh_tool.sh -o ssh_tool.sh && chmod +x ssh_tool.sh && ./ssh_tool.sh
```

* 线路脚本：
```
wget -qO- git.io/besttrace | bash
```
