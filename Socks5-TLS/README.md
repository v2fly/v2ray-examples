## SOCKS5 / TLS

### 安全提示
该配置组合应仅供技术研究/参考使用，因为 SOCKS5 / TLS 的组合**极易受到主动探测**。

根据 [RFC1929](https://tools.ietf.org/html/rfc1929) 所叙，服务器对 SOCKS5 鉴权的返回格式如下：

```
   The server verifies the supplied UNAME and PASSWD, and sends the
   following response:

                        +----+--------+
                        |VER | STATUS |
                        +----+--------+
                        | 1  |   1    |
                        +----+--------+

   A STATUS field of X'00' indicates success. If the server returns a
   `failure' (STATUS value other than X'00') status, it MUST close the
   connection.
```

如此，向可疑服务器建立 TLS 链接之后，随意发送一个鉴权请求，即可通过回包的格式断定该服务是否是 SOCKS5 / TLS。
