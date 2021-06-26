# VLESS-gRPC-TLS

## VLESS-gRPC-TLS-web

### Nginx

1. In [config_server.json](config_server.json): Remove `tlsSettings`, Change `security` to `none` or simply remove it. Change Inbound listen to 127.0.0.1 or Unix Domain Socket.

2. In nginx config: Listen http2, add location `GunService` (should same as grpc `serviceName`).

Config clip example:

<details>

<summary>v2ray</summary>

> `/etc/v2ray/config.json` (server side)

```json
{
    "log": {
        "loglevel": "warning"
    },
    "inbounds": [
        {
            "listen": "127.0.0.1",
            "port": 9000,
            "protocol": "vless",
            "settings": {
                "clients": [
                    {
                        "id": "",
                        "email": "love@v2fly.org"
                    }
                ],
                "decryption": "none"
            },
            "streamSettings": {
                "network": "gun",
                "grpcSettings": {
                    "serviceName": "GunService"
                }
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom",
            "tag": "direct"
        }
    ]
}
```

</details>

<details>

<summary>nginx</summary>

> `/etc/nginx/conf.d/yourdomain.conf`

```nginx
server {
    # ......
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    # ......
    location /GunService/Tun {
        if ($request_method != "POST" ) {
            return 404;
        }
        client_max_body_size 0;
        client_body_timeout 1h;
        grpc_read_timeout 1h;
        grpc_pass grpc://127.0.0.1:9000;
        grpc_set_header X-Real-IP $http_x_forwarded_for;
        grpc_set_header X-Forwarded-For $proxy_protocol_addr;
    }
    # ......
}
```

</details>
