# 最低版本要求

NGINX 的最低版本要求为 1.13.10:\
[https://www.nginx.com/blog/nginx-1-13-10-grpc/](https://www.nginx.com/blog/nginx-1-13-10-grpc/)

V2Ray-core 的最低版本要求为 v4.36.0:\
[https://www.v2fly.org/config/transport/grpc.html#grpcobject](https://www.v2fly.org/config/transport/grpc.html#grpcobject)

## 本设置同样适用于 Shadowsocks 客户端搭配 V2Ray-plugin 使用

_你需要一个兼容 gRPC 的 v2ray-plugin 程序。
例如由[TeddySun](https://github.com/teddysun)维护的 v2ray-plugin 叉子: \
[https://github.com/teddysun/v2ray-plugin](https://github.com/teddysun/v2ray-plugin)_

### 客户端设置

Shadowsocks Windows 设置示例:

```properties
Server_IP: mydomain.me OR your server IP
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: tls;mode=grpc;serviceName=michi;host=mydomain.me
```
