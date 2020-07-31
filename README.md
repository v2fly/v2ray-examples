# vTemplate

这是一个社会实验性质的项目，提供数种常见的 V2Ray 配置模板

早些时间雨落无声大佬的 [v2ray.fun](https://github.com/FunctionClub/v2ray.fun) 宣布弃坑，再次引发了 V2Ray 水群里大佬关于一键脚本和伸手党的讨论。在讨论过程中，提出了一个有趣的命题：

一键脚本是否会助长伸手之风？如果会，我们不提供一键脚本而只提供模板的话，情况是否又会好些？

于是，这个项目就诞生了。在这里收录一些常用的 V2Ray 配置模板，这些配置多由 v2ray.fun 生成，在这基础上加上少许改动。<br>
在你套用模板之前，请先仔细阅读 [V2Ray 官方文档](https://v2fly.org)，如果可能，尽量尝试不借助模板自己编写配置文件，以加深对配置的理解。

如果你在配置过程中遇到问题，请再看一遍[文档](https://v2fly.org)，或是在 Google 搜索以求自己解决问题。当你确认你的问题无法独立解决时，你可以在 V2Ray 的 Telegram 群组里求助，或是在 V2Ray 官方的 [discussion](https://github.com/v2ray/discussion) 项目中提交 issue。<br>
遇事不决，请 RTFM/STFW。

## 如何选取适合自己的配置：

![](How_To_Choose.jpg)

附加说明：<br>
尽管 Websocket+TLS+Web 可能称得上是现阶段最好的方案，但**绝对**不是推荐新手一上来就尝试的方案，更不是 V2Ray 唯一的用法。<br>
同时，你应当了解，每个地区的网络状况不同 (主要指对不同协议的 QoS 程度)，你可以将所有配置都尝试一遍来寻找最适合自己的，尽量少问、最好不问“为什么我的 V2Ray 这么慢？”这样的问题。

## 贡献指南

V2Ray 有着活跃的生态，那么此模板仓库也应该是如此，许久不更新的配置可能会存在一些问题。因此欢迎你将自己使用的配置制作模板，提交 PR。模板应遵守以下标准：

1. 一切配置文件从[模板](#模板)展开。
2. 每一层级缩进 2 空格。
3. 方 (花) 括号不换行。
4. 不需要的字段应该移除，例如 TCP 配置中的 `kcpSettings`。
5. 考虑到 Windows，`log` 部分只留 `loglevel`。
6. 针对 `outbounds`，客户端应有 `proxy` 和 `direct`，服务端应有 `direct` 和 `block`。
7. 除非专门的路由模板，否则只处理 `geoip:private` 到 `direct` (服务端处理到 `block`)，或者不要路由。
8. 除非特定场景的模板，配置文件中应不写 DNS。
9. `uuid` 应留空，由用户自行填写。
10. `routing` 中的 `domainStrategy` 保持默认，即 `AsIs`。
11. 此项目中应无同种目的 / 场景的模板。

举例，以下是符合标准的配置文件：

### 模板

```json
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

```json
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
        "port": null,
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
            "id": "e2b39869-7e9e-411b-a561-00904419bed9",
            "alterId": 100,
            "testsEnabled": "VMessAEAD"
          }
        ]
      },
      "tag": "tcp",
      "streamSettings": {
        "network": "tcp"
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "freedom",
      "settings": {
      },
      "tag": "direct"
    }
  ]
}
```

### 服务端

```json
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
        "port": null,
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
            "id": "e2b39869-7e9e-411b-a561-00904419bed9",
            "alterId": 100,
            "testsEnabled": "VMessAEAD"
          }
        ]
      },
      "tag": "tcp",
      "streamSettings": {
        "network": "tcp"
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "freedom",
      "settings": {
      },
      "tag": "direct"
    },
    {
      "protocol": "blackhole",
      "settings": {
      },
      "tag": "blocked"
    }
  ]
}
```

## 最后

祝你玩的愉快，感谢 Project V 的所有开发人员，以及 v2ray.fun 的作者雨落无声。
