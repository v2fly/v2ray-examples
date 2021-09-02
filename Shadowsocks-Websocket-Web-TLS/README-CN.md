# 这个例子同样适用于 Shadowsocks 客户端+V2Ray-Plugins

> 完整的设置还需要一个 web 服务器解密 TLS 后,将请求转发给监听在 127.0.0.1:10000 的 v2ray。由于 [https://guide.v2fly.org/advanced/wss_and_web.html#%E9%85%8D%E7%BD%AE](https://guide.v2fly.org/advanced/wss_and_web.html#%E9%85%8D%E7%BD%AE) 已经有了服务器的设置这里不再赘述，可以按需参考白话文教程里的 web 服务器设置。

## 客户端配置示意

你应该按照服务端的设置修改对应的参数

### shadowsocks windows 客户端关键部分示例如下

> 必须设置 mux=0，否则无法正常连接服务器。如果需要使用 mux 可以参考本文件夹里的[Domainsocket or Redirect Approach](./Domainsocket-or-Redirect-Approach/)的方法。

```properties
Server_IP: example.com or your server ip
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: mux=0;tls;mode=websocket;path=/path;host=example.com
```

### Shadowsocks Android plugin 关键部分示例如下

> 需安装 shadowsocks 和 v2ray plugin，并搭配一同使用。
> Concurrent connections 必须为 0，否则无法连接到服务器。

```properties
Plugin: v2ray
Configuration:
    Transport_mode: websocket-tls
    Hostname: example.com
    Path: /path
    Concurrent_connections: 0
    Certificate_for_TLS_verification: Not set
```
