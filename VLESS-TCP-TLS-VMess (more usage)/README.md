# VLESS over TCP with TLS + 回落 & 分流 to TCP（更多玩法）

这里是 [推荐配置](<https://github.com/v2fly/v2ray-examples/tree/master/VLESS-TCP-TLS%20(minimal%20by%20rprx)>) 的补充，利用 VLESS 强大的回落分流特性，实现了 443 端口 VLESS & VMess over TCP with TLS 的完美共存

你还可以配置回落到 Caddy 的 forwardproxy 等其它防探测的代理，以及分流到任何支持 WebSocket 的代理，都没有问题
