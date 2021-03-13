# PUBLICTEXT
[UCSPI-TCP](http://cr.yp.to/ucspi-tcp.html "UNIX Client-Server Program Interface for TCP") [TEXT://PROTOCOL](https://textprotocol.org "TEXT://PROTOCOL") [server](http://cr.yp.to/ucspi-tcp/tcpserver.html "tcpserver")

```bash
# echo -e 'text://txt.textprotocol.org/\r\n' | nc txt.textprotocol.org 1961
20 text/plain; charset=utf-8
Hello text://protocol! ✌︎

=> geo:37.429167,-122.138056 PALO ALTO, CA 94301, USA
=> tag:txt.textprotocol.org,2021:1961-1965-1968 tag
=> text://txt.textprotocol.org/icon.png rel=icon
=> text://txt.textprotocol.org/license.txt rel=license CC0-1.0
=> text://txt.textprotocol.org/pgp.asc rel=pgpkey
=> text://txt.textprotocol.org/robots.txt rel=robots
```

```bash
openssl s_client -quiet -crlf -connect txt.textprotocol.org:1965 <<< text://txt.textprotocol.org/ 2>/dev/null | head -1
20 text/plain; charset=utf-8
```
