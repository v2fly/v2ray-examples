# VMess: WebSocket + TLS + Web (nginx)

来自[新 V2Ray 白话文指南](https://guide.v2fly.org/advanced/wss_and_web.html)的WebSocket+TLS+Web配置，使用nginx作为服务器。

配置文件中的以下字段需要替换：

- `V2RAY_PORT`：任意有效的端口，只在`127.0.0.1`监听。
- `V2RAY_UUID`：VMess的UUID。
- `PATH`：WS请求的路径，形如`/nginx`等的字符串。
- `DOMAIN_NAME`：你的域名。
- `CERT`：TLS证书。
- `KEY`：TLS的Key。

