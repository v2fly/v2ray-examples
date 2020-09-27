# VLESS over TCP with XTLS + 回落 & 分流 to WHATEVER（终极配置）

这里是 [进阶配置](<https://github.com/v2fly/v2ray-examples/tree/master/VLESS-TCP-TLS-WS%20(recommended)>) 的超集，利用 VLESS 强大的回落分流特性，实现了 443 端口尽可能多的协议、配置的完美共存，包括 [XTLS](https://www.v2fly.org/config/protocols/vless.html#xtls-%E9%BB%91%E7%A7%91%E6%8A%80)

客户端可以同时通过下列方式连接到服务器，其中 WS 都可以通过 CDN

1. VLESS over TCP with XTLS
2. VLESS over TCP with TLS
3. VLESS over WS with TLS
4. VMess over TCP with TLS
5. VMess over WS with TLS

---

你还可以配置回落到 Caddy 的 forwardproxy 等其它也防探测的代理，以及分流到任何支持 WebSocket 的代理，都没有问题
