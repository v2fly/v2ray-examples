# This is the server config.json example to utilizing V2ray as the server for Shadowsocks + V2Ray Plugin
> The complete setup also requires a web server to handle the TLS and proxy pass the deciphered request to the backend v2ray server at 127.0.0.1:10000.
> You can find the web server example at https://guide.v2fly.org/en_US/advanced/wss_and_web.html#server-side-configuration 

中文用户请看 Readme - zh-CN. md

**Choose either one of config_server_redirect.json and config_server_domainsocket.json**

If you choose to use config_server_domainsocket.json remember to modify the systemd service file @ /etc/systemd/system/v2ray.service.

Add the following line to the block starting with [Service]
```
RuntimeDirectory=ss-loop 
```
'ss-loop' corresponds to the "/var/run/ss-loop" folder in the "dsSettings" part of the config.json.

Execute the following commands to re-enable the v2ray.service.
```
systemctl disable v2ray.service
systemctl enable v2ray.service
```
Since nobody user does not have the right permission to create the 'ss-loop' folder in /var/run.
## Client configuration examples
**You should change the parameters according to your server configs**
### shadowsocks windows client configuration examples：
```
Server IP: example.com
Server Port: 443
Password: ifYouWantToKeepYourPassphraseSafeChangeThis!!
Encryption: chacha20-ietf-poly1305
Plugin Program: pathToYourV2ray-plugin_windows_arch.exe
Plugin Options: tls;mode=websocket;path=/michi;host=example.com
```
### shadowsocks Android plugin configuration examples：

> Both the shadowsocks android and the V2Ray plugin android are mandatory, they are available on Google Play Store.
```
Plugin: v2ray
Configuration:
    Transport mode: websocket-tls
    Hostname: example.com
    Path: /michi
    Concurrent connections: 1
    Certificate for TLS verification: Not set
```
