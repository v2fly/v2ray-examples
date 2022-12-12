# v2ray-examples

![ENGLISH Here are some V2Ray configuration examples for reference](README.ENG.md)

这里是一些供参考的 V2Ray 配置示例，内容与时俱进，自动化脚本等请勿从这里拉取配置。

感谢 vTemplate 的作者 KiriKira、雨落无声和 Project V 的所有开发人员。

## 贡献指南

欢迎你将自己使用的配置制作模板，提交 PR。

模板应遵守以下标准：
- 缩进使用 4 个空格
- 方 (花) 括号不换行
- 不需要的字段应该移除
- `log` 部分只留 `loglevel`
- 对于 `outbounds`，客户端应有 `proxy` 和 `direct`，服务端应有 `direct` 和 `block`
- 除非是适用于特定场景的模板，否则应当将 `geoip:private` 路由到 `direct` 出站 (服务端配置路由到 `block` 出站)
- 除非是适用于特定场景的模板，否则配置文件中不应出现 DNS
- `uuid` 应留空，由用户自行填写。
- `routing` 中的 `domainStrategy` 保持默认，即 `AsIs`。

### 举例

<!-- 此处 yaml 仅用作语法高亮，实际内容为 json -->
```yaml
{
    "log": {
        "loglevel": "warning"
    },
    "routing": {},
    "inbounds": [],
    "outbounds": []
}
```

### 客户端

<!-- 此处 yaml 仅用作语法高亮，实际内容为 json -->
```yaml
{
    "log": {
        "loglevel": "warning"
    },
    "routing": {
        "domainStrategy": "AsIs",
        "rules": [
            {
                "ip": [
                    "geoip:private"
                ],
                "outboundTag": "direct",
                "type": "field"
            }
        ]
    },
    "inbounds": [
        {
            "port": 1080,
            "protocol": "socks",
            "settings": {
                "auth": "noauth",
                "udp": true
            },
            "tag": "socks"
        }
    ],
    "outbounds": [
        {
            "protocol": "vmess",
            "settings": {
                "vnext": [
                    {
                        "users": [
                            {
                                "id": ""
                            }
                        ],
                        "port": 1234,
                        "address": "Your_IP_Address"
                    }
                ]
            }
        },
        {
            "protocol": "freedom",
            "tag": "direct"
        }
    ]
}
```

### 服务端

<!-- 此处 yaml 仅用作语法高亮，实际内容为 json -->
```yaml
{
    "log": {
        "loglevel": "warning"
    },
    "routing": {
        "domainStrategy": "AsIs",
        "rules": [
            {
                "ip": [
                    "geoip:private"
                ],
                "outboundTag": "blocked",
                "type": "field"
            }
        ]
    },
    "inbounds": [
        {
            "port": 1234,
            "protocol": "vmess",
            "settings": {
                "clients": [
                    {
                        "id": "",
                    }
                ]
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom"
        },
        {
            "protocol": "blackhole",
            "tag": "blocked"
        }
    ]
}
```

## 如何选取适合自己的配置：

![](how-to-choose/how-to-choose-a-v2ray-plan.png)

附加说明：<br>
尽管 Websocket+TLS+Web 可能称得上是现阶段最好的方案，但**绝对**不是推荐新手一上来就尝试的方案，更不是 V2Ray 唯一的用法。<br>
同时，你应当了解，每个地区的网络状况不同 (主要指对不同协议的 QoS 程度)，你可以将所有配置都尝试一遍来寻找最适合自己的，尽量少问、最好不问“为什么我的 V2Ray 这么慢？”这样的问题。

## 最后

祝你玩的愉快！
