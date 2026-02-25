# This is the server config.json example to utilizing V2ray as the server for Shadowsocks + V2Ray Plugin

> The complete setup also requires a web server to handle the TLS and proxy pass the deciphered request to the backend v2ray server at 127.0.0.1:10000.
> You can find the web server config example at [https://guide.v2fly.org/en_US/advanced/wss_and_web.html#server-side-configuration](https://guide.v2fly.org/en_US/advanced/wss_and_web.html#server-side-configuration).

中文用户请看[这里](./README-CN.md)。

Choose one of the server config `config_server_redirect.json` and `config_server_domainsocket.json`.

If you choose to use `config_server_domainsocket.json`, the following extra steps are required. Since the default service file created by [`fhs-release.sh`](https://github.com/v2fly/fhs-install-v2ray) is using nobody as the runtime user, this user does not have the permission to create the `ss-loop` folder in `/var/run`.

> You shall repeat the following steps after using [`fhs-release.sh`](https://github.com/v2fly/fhs-install-v2ray) scripts to upgrade v2ray-core versions each time. Since this script will always override the v2ray.service file.

Use your prefered editor to modify the systemd service file at `/etc/systemd/system/v2ray.service`.\
Add the following line to the block starting with `[Service]`.

```properties
RuntimeDirectory=ss-loop
```

`ss-loop` corresponds to the `/var/run/ss-loop` folder in the `dsSettings` inside config_server_domainsocket.json.

Execute the following commands to re-enable the v2ray.service.

```shell
systemctl disable v2ray.service
systemctl enable v2ray.service
```

Then restart the v2ray service.

```shell
systemctl restart v2ray
```

## Client configuration examples

> You should change the following configurations according to your server configs.

### shadowsocks windows client configuration examples

```properties
Server_IP: example.com or your server IP
Server_Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin_Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin_Options: tls;mode=websocket;path=/michi;host=example.com
```

### shadowsocks Android plugin configuration examples

> Both the shadowsocks android and the V2Ray plugin android are mandatory, they are available on Google Play Store.

```properties
Plugin: v2ray
Configuration:
    Transport_mode: websocket-tls
    Hostname: example.com
    Path: /michi
    Concurrent_connections: 1
    Certificate_for_TLS_verification: Not set
```
