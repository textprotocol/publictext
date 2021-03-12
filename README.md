# publictext
[ucspi-tcp](http://cr.yp.to/ucspi-tcp.html "UNIX Client-Server Program Interface for TCP") [text://protocol](https://textprotocol.org "TEXT://PROTOCOL") [server](http://cr.yp.to/ucspi-tcp/tcpserver.html "tcpserver")

```bash
#
# publictext: ucspi-tcp text://protocol server
#

# tree --noreport
.
├── bin
│   └── publictext
├── etc
└── var
    ├── log
    └── txt
        ├── icon.png
        ├── index.txt
        ├── license.txt
        └── robots.txt

# wc -l bin/publictext
     155 bin/publictext

# head -1 bin/publictext
#!/usr/bin/env lua

# cd var/txt

# ../../bin/publictext <<< 'text://' 2>/dev/null | head -1
20 text/plain; charset=utf-8

# ../../bin/publictext <<< 'text://' 1>/dev/null
- - - [11/Mar/2021:11:11:11 +0000] "text://" 20 234

# tcpserver -v -c42 -o -D -H -P -l 0 -R 127.0.0.1 1961 timeout 1 ../../bin/publictext

# echo -e 'text://127.0.0.1/\r\n' | nc 127.0.0.1 1961 | head -1
20 text/plain; charset=utf-8

# echo -e 'text://127.0.0.1/foobarbaz\r\n' | nc 127.0.0.1 1961 | head -1
40 NOK
```

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
# echo -e 'gemini://txt.textprotocol.org/\r\n' | nc txt.textprotocol.org 1961
20 text/plain; charset=utf-8
Hello gemini://protocol! ✌︎

=> geo:37.429167,-122.138056 PALO ALTO, CA 94301, USA
=> tag:textprotocol.org,2021:1961-1965-1968-GMI tag
=> gemini://txt.textprotocol.org/icon.png rel=icon
=> gemini://txt.textprotocol.org/license.txt rel=license CC0-1.0
=> gemini://txt.textprotocol.org/pgp.asc rel=pgpkey
=> gemini://txt.textprotocol.org/robots.txt rel=robots
```

```bash
openssl s_client -quiet -crlf -connect txt.textprotocol.org:1965 <<< text://txt.textprotocol.org/ 2>/dev/null | head -1
20 text/plain; charset=utf-8
```

```bash
openssl s_client -quiet -crlf -connect txt.textprotocol.org:1965 <<< gemini://txt.textprotocol.org/ 2>/dev/null | head -1
20 text/plain; charset=utf-8
```
