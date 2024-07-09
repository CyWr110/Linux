# Linux


* 必要更新操作(Debian/Ubuntu)
```
apt update -y && apt install -y curl socat wget
```

* VPS系统更新
```
apt update
```

* Kejilion一键脚本
```
curl -sS -O https://kejilion.pro/kejilion.sh && chmod +x kejilion.sh && ./kejilion.sh
```

* xui脚本：
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

* 一键安装宝塔面板（非国际版）
```
wget -O install.sh https://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh ed8484bec
```

* warp脚本：
```
wget -N https://gitlab.com/fscarmen/warp/-/raw/main/menu.sh && bash menu.sh [option] [lisence/url/token]
```
再次启动：
```
warp [option] [lisence]
```

* 国外vps安装Dcoker
```
curl -fsSL https://get.docker.com | bash -s docker 
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
bash <(curl -L -s media.ispvps.com)
```

* 一键搭建SS节点
```
wget -O ss-rust.sh --no-check-certificate https://raw.githubusercontent.com/xOS/Shadowsocks-Rust/master/ss-rust.sh && chmod +x ss-rust.sh && ./ss-rust.sh
```

* Hy2节点搭建一键脚本

```
wget -N --no-check-certificate https://raw.githubusercontent.com/Misaka-blog/hysteria-install/main/hy2/hysteria.sh && bash hysteria.sh
```

* Snell 节点搭建 一键脚本
```
curl -sS -o Snell.sh https://raw.githubusercontent.com/passeway/Snell/main/Snell.sh && chmod +x Snell.sh && ./Snell.sh
```

* Snell V4

```
wget -O snell.sh --no-check-certificate https://git.io/Snell.sh && chmod +x snell.sh && ./snell.sh
```

* 网速测试 配置测试
```
curl -L https://gitlab.com/spiritysdx/za/-/raw/main/ecs.sh -o ecs.sh && chmod +x ecs.sh && bash ecs.sh
```
