# Minimum Versions

中文用户请看[这里](./README-CN.md)

Minimum NGINX version is 1.13.10:\
[https://www.nginx.com/blog/nginx-1-13-10-grpc/](https://www.nginx.com/blog/nginx-1-13-10-grpc/)

Minimum V2Ray-Core version is v4.36.0:\
[https://www.v2fly.org/config/transport/grpc.html#grpcobject](https://www.v2fly.org/config/transport/grpc.html#grpcobject)

## These settings are also compatible with shadowsocks + v2ray-plugins

*You need a grpc compatible v2ray-plugin program to use with shadowsocks client.
For example the one maintained by [TeddySun](https://github.com/teddysun): \
[https://github.com/teddysun/v2ray-plugin](https://github.com/teddysun/v2ray-plugin)*

### Client Configurations

Shadowsocks Windows Example Config:

```properties
Server_IP: mydomain.me OR your server IP
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: tls;mode=grpc;serviceName=/michi;host=mydomain.me
```
