# 最低版本要求

NGINX的最低版本要求为 1.13.10:\
[https://www.nginx.com/blog/nginx-1-13-10-grpc/](https://www.nginx.com/blog/nginx-1-13-10-grpc/)

V2Ray-core的最低版本要求为 v4.36.0:\
[https://www.v2fly.org/config/transport/grpc.html#grpcobject](https://www.v2fly.org/config/transport/grpc.html#grpcobject)

## 本设置同样适用于Shadowsocks客户端搭配V2Ray-plugin使用

*你需要一个兼容gRPC的v2ray-plugin程序。
例如由[TeddySun](https://github.com/teddysun)维护的v2ray-plugin叉子: \
[https://github.com/teddysun/v2ray-plugin](https://github.com/teddysun/v2ray-plugin)*

### 客户端设置

Shadowsocks Windows设置示例:

```properties
Server_IP: mydomain.me OR your server IP
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: tls;mode=grpc;serviceName=/michi;host=mydomain.me
```
