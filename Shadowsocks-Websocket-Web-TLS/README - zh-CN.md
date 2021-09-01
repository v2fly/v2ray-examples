# 这是一个使用 V2Ray 作为 ss + v2ray plugin 服务端的示例
> 完整的设置还需要一个web服务器解密TLS后将请求转发给后端的v2ray位于127.0.0.1:10000。由于 https://guide.v2fly.org/advanced/wss_and_web.html#%E9%85%8D%E7%BD%AE 已经有了服务器的设置这里不再赘述，可以按需参考白话文教程里的web服务器设置。

**config_server_redirect.json 和 config_server_domainsocket.json 选其一**

如果使用domain socket需要修改/etc/systemd/system/v2ray.service
在[Service]部分添加
```
RuntimeDirectory=ss-loop 
```
'ss-loop'对应config.json里的"dsSettings"部分的path里的文件夹"/var/run/ss-loop"

修改完成后需要执行
```
systemctl disable v2ray.service
systemctl enable v2ray.service
```
否则由于fhs脚本使用的nobody用户的权限不够，无法在/var/run里新建文件夹'ss-loop'而导致启动失败。

## 客户端配置示意
**你应该按照服务端的设置修改对应的参数**
### shadowsocks windows 客户端关键部分示例如下：
```
Server IP: example.com
Server Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin Options: tls;mode=websocket;path=/michi;host=example.com
```
### shadowsocks Android plugin 关键部分示例如下：

**需安装 shadowsocks 和 v2ray plugin，并搭配一同使用**
```
Plugin: v2ray
Configuration:
    Transport mode: websocket-tls
    Hostname: example.com
    Path: /michi
    Concurrent connections: 1
    Certificate for TLS verification: Not set
```
