# PUBLICTEXT
[UCSPI-TCP](http://cr.yp.to/ucspi-tcp.html "UNIX Client-Server Program Interface for TCP") [TEXT://PROTOCOL](https://textprotocol.org "TEXT://PROTOCOL") [SERVER](http://cr.yp.to/ucspi-tcp/tcpserver.html "TCPSERVER")

```bash
#
# publictext
# ucspi-tcp text://protocol server
#

# tree
.
├── bin
│   └── publictext
├── etc
└── var
    ├── log
    └── txt
        ├── icon.png
        ├── index.txt
        └── license.txt
```

```bash
# cd var/txt

# ../../bin/publictext <<< 'text://' 2>/dev/null | head -1
20 text/plain; charset=utf-8

# ../../bin/publictext <<< 'text://' 1>/dev/null
- - - [11/Mar/2021:11:11:11 +0000] "text://" 20 234

# tcpserver -v -c42 -o -D -H -P -l 0 -R 127.0.0.1 1961 timeout 1 ../../bin/publictext

# nc -C 127.0.0.1 1961 <<< 'text://127.0.0.1/' | head -1
20 text/plain; charset=utf-8

# nc -C 127.0.0.1 1961 <<< 'text://127.0.0.1'
30 text://127.0.0.1/

# nc -C 127.0.0.1 1961 <<< 'text://127.0.0.1/foo.bar'
40 NOK
```

```bash
# nc -C txt.textprotocol.org 1961 <<< 'text://txt.textprotocol.org/'
20 text/plain; charset=utf-8
TEXT://PROTOCOL

=> geo:37.429167,-122.138056 PALO ALTO, CA 94301, USA
=> tag:txt.textprotocol.org,2021-03-07:textprotocol@github rel=me
=> text://txt.textprotocol.org/icon.png rel=icon
=> text://txt.textprotocol.org/license.txt rel=license CC0-1.0

—
🆃🆇🆃
```
