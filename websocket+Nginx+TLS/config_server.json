{
  "log": {
    "access": "/var/log/v2ray/access.log", 
    "error": "/var/log/v2ray/error.log", 
    //可能取值 "debug" "info" "warning" "error" 其中"debug"记录的数据最多，"error"记录的最少 "none"表示不记录任何内容 默认值为"warning"
    "loglevel": "debug" 
  },
  //注"policy"字段需要core≥3.1
  "policy": {
    "levels": {
      "0": {
        "uplinkOnly": 0,
        "downlinkOnly": 0,
        "connIdle": 150,
        "handshake": 4
      }
    }
  },
  "inbound": {
    //默认值为"0.0.0.0"
    "listen": "127.0.0.1", 
    "port": 10086, 
    "protocol": "vmess", 
    "settings": {
      "clients": [
        {
          "id": "7f43b638-dc47-11e7-9296-cec278b6b50a",
          //"level"字段与"policy"字段中的"levels"字段中的对应，默认值:0,注：需要core≥3.1
          "level": 0, 
          "alterId": 64
        }
      ]
    }, 
    "streamSettings": {
      "network": "ws", 
      "security": "auto", 
      "wsSettings": {
        "path": "/PATH/", 
        "headers": {
          "Host": "domain.Name"
        }
      }
    }
  }, 
  "outbound": {
    "protocol": "freedom", 
    "settings": { }
  }, 
  "outboundDetour": [
    {
      "protocol": "blackhole", 
      "settings": { }, 
      "tag": "blocked"
    }
  ], 
  "routing": {
    "strategy": "rules", 
    "settings": {
      "rules": [
        {
          "type": "field", 
          "ip": [
            "0.0.0.0/8", 
            "10.0.0.0/8", 
            "100.64.0.0/10", 
            "127.0.0.0/8", 
            "169.254.0.0/16", 
            "172.16.0.0/12", 
            "192.0.0.0/24", 
            "192.0.2.0/24", 
            "192.168.0.0/16", 
            "198.18.0.0/15", 
            "198.51.100.0/24", 
            "203.0.113.0/24", 
            "::1/128", 
            "fc00::/7", 
            "fe80::/10"
          ], 
          "outboundTag": "blocked"
        }
      ]
    }
  }
}
