# VLESS TCP over TLS + 回落 & 分流 to WebSocket（推荐配置）

这里是 [最简配置](<https://github.com/v2fly/v2ray-examples/tree/master/VLESS-TCP-TLS%20(minimal%20by%20rprx)>) 的超集，利用 VLESS 强大的回落分流特性，实现了 443 端口 VLESS TCP over TLS 和任意 WSS 的完美共存

该配置供参考，你可以将 WS 上的 VLESS 换成 VMess 等其它任何协议，以及设置更多 PATH、协议共存，都可以做到

部署后，你可以同时通过 VLESS TCP over TLS 和任意 WebSocket over TLS 方式连接到服务器，其中后者都可以通过 CDN

经实测，VLESS 回落分流 WS 比 Nginx 反代 WS 性能更强，传统的 VMess + WSS 方案完全可以迁移过来，且不失兼容
