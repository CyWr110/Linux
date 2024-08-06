# DDNS动态域名设置

* 下载 DNNS 脚本：
```
curl https://raw.githubusercontent.com/CyWr110/Linux/main/DDNS/cf-v4-ddns.sh > /root/cf-v4-ddns.sh && chmod +x /root/cf-v4-ddns.sh
```

* 修改 DDNS 脚本并补充相关信息：
```
vi cf-v4-ddns.sh
```
或者直接打开/root/cf-v4.ddns.sh文件编辑修改后保存

* 填写 CF全局Global API Key
CFKEY=

* 填写 CloudFlare 登陆邮箱
CFUSER=

* 填写需要用来 DDNS 的一级域名
CFZONE_NAME=

* 填写 DDNS 的二级域名(只需填写前缀)
CFRECORD_NAME=

* 首次运行脚本，输出内容会显示当前 IP，进入 cloudflare 查看 确保 IP 已变更为当前 IP
```
./cf-v4-ddns.sh
```
* 设置定时任务
```
crontab -e
```
* 设置每2分钟自动运行一次
```
*/2 * * * * /root/cf-v4-ddns.sh >/dev/null 2>&1
```
