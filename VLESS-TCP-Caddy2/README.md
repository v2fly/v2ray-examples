# Vless 自动回落到 Caddy2

## 准备

你需要有一个解析到服务器 IP 的域名，替换文档中的 example.com
Vless 将使用 Caddy 申请的证书，无需额外配置
将你的自建网站放置于 /var/www/html 路径

## Caddy2 安装

[https://caddyserver.com/docs/download#debian-ubuntu-raspbian]()

## v2ray 读取证书失败

修改证书 key 文件的权限为 644
[https://github.com/v2fly/fhs-install-v2ray/wiki/Insufficient-permissions-when-using-certificates-zh-Hans-CN]()