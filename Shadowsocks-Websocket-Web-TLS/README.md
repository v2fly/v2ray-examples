# These settings are also compatible with Shadowsocks client + V2Ray-plugin

> The complete setup also requires a web server to handle the TLS and proxy pass the deciphered request to the backend v2ray server listeing on 127.0.0.1:10000.
> You can find the web server config examples at [https://guide.v2fly.org/en_US/advanced/wss_and_web.html#server-side-configuration](https://guide.v2fly.org/en_US/advanced/wss_and_web.html#server-side-configuration).

中文用户请看[这里](./README-CN.md)。

## Shadowsocks client configuration examples

> You should change the following configurations according to your server configs.

### Shadowsocks windows client configuration examples

> `mux=0` is indispensable when connecting with V2Ray-plugin, if you wish to use mux you need to try the [Domainsocket or Redirect Approach](./Domainsocket-or-Redirect-Approach/).

```properties
Server_IP: example.com or your server IP
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: mux=0;tls;mode=websocket;path=/path;host=example.com
```

### shadowsocks Android plugin configuration examples

> Both the shadowsocks android and the V2Ray plugin android are mandatory, they are available on Google Play Store.\
> _`Concurrent connections must be 0.`_

```properties
Plugin: v2ray
Configuration:
    Transport_mode: websocket-tls
    Hostname: example.com
    Path: /path
    Concurrent_connections: 0
    Certificate_for_TLS_verification: Not set
```
