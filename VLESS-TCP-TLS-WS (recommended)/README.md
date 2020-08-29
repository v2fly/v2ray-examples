# VLESS + TCP + TLS + 回落 + WebSocket（推荐配置）

这里是 [最简配置](<https://github.com/v2fly/v2ray-examples/tree/master/VLESS-TCP-TLS%20(minimal%20by%20rprx)>) 的超集，利用 VLESS 强大的回落特性，实现了 443 端口 TCP & WS 的完美共存

部署后，你可以同时通过 TCP + TLS 和 WS + TLS 方式连接到服务器，其中 WS 还可以通过 CDN

经实测，VLESS 回落分流 WS 比 Nginx 反代 WS 性能更强，传统的 WSS 方案完全可以切换过来

你还可以将 WS 上的 VLESS 换成 VMess 等其它任何协议，以及设置更多协议共存，都可以做到
