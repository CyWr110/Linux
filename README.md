# Linux


* DD debian 11 萌咖
```
wget -N --no-check-certificate https://raw.githubusercontent.com/veip007/dd/master/InstallNET.sh && chmod +x InstallNET.sh && ./InstallNET.sh -d 11 -v 64 -p <自定义密码> -port <自定义端口>
```
* DD脚本 (秋水逸冰 改自 萌咖)
```
bash <(wget --no-check-certificate -qO- 'qiu.sh/dd') -d 12 -v 64 -p <自定义密码> -port <自定义端口>
```

* 必要更新操作(Debian/Ubuntu)
```
apt update -y && apt install -y curl socat wget
```

* 国外vps安装Dcoker
```
curl -fsSL https://get.docker.com | bash -s docker 
```

* Mack-A八合一共存脚本
```
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

* Kejilion一键脚本
```
curl -sS -O https://kejilion.pro/kejilion.sh && chmod +x kejilion.sh && ./kejilion.sh
```

* Debian/Ubuntu安装下载工具
```
apt update -y  && apt install -y curl
```

* Debian/Ubuntu Docker 安装官方一键脚本

```
 curl -fsSL https://get.docker.com -o get-docker.sh
 sudo sh get-docker.sh
```

* 流媒体解锁查询
```
bash <(curl -L -s check.unlock.media)
```

* 一键安装多种协议的节点
```
bash <(wget -qO- https://raw.githubusercontent.com/fscarmen/argox/main/argox.sh)
```

* v2Ray安装脚本
```
bash <(wget -qO- -o- https://git.io/v2ray.sh)
```

* snell v4一键搭建脚本
```
wget -O snell.sh --no-check-certificate https://git.io/Snell.sh && chmod +x snell.sh && ./snell.sh
```

* snell 一键搭建脚本


 安装
```
sudo bash -c "$(curl -sL https://raw.githubusercontent.com/CCCOrz/auto-snell/main/install.sh)"
```
 卸载
```
sudo bash -c "$(curl -sL https://raw.githubusercontent.com/CCCOrz/auto-snell/main/uninstall.sh)"
```


* 一键搭建SS节点
```
wget -O ss-rust.sh --no-check-certificate https://raw.githubusercontent.com/xOS/Shadowsocks-Rust/master/ss-rust.sh && chmod +x ss-rust.sh && ./ss-rust.sh
```

* Hy2节点搭建一键脚本（第一种Surge可以直接用）
```
bash <(curl -Ls https://raw.githubusercontent.com/passeway/Hysteria/main/Hysteria2.sh)
```

```
wget -N --no-check-certificate https://raw.githubusercontent.com/Misaka-blog/hysteria-install/main/hy2/hysteria.sh && bash hysteria.sh
```

* Snell 节点搭建 一键脚本
```
curl -sS -o Snell.sh https://raw.githubusercontent.com/passeway/Snell/main/Snell.sh && chmod +x Snell.sh && ./Snell.sh
```

* 网速测试 配置测试
```
curl -L https://gitlab.com/spiritysdx/za/-/raw/main/ecs.sh -o ecs.sh && chmod +x ecs.sh && bash ecs.sh
```
