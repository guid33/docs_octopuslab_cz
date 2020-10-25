# ![logo](img/logo_small.png) FTP


**FTP** (File transfer protocol) - protokol pro přenos souborů mezi počítači pomocí počítačové sítě.

Původní knihovna pro ESP8266 i ESP32 v základu funguje. 
Používáme například FTP plugin **Total Commanderu** (testováno ve Win 10).

Jednoduchá verze - na ESP běží samostatně "pouze" FTP. Po připojení k lokální síti se spustí FTP a vypíše IP adresu.


```python
>>> from utils.octopus_lib import w
>>> w() # wifi connect

>>> import ftp
>>> ftp
FTP Server started on  192.168.x.x # -> IP

```

---

V Total Commanderu (přes `CTRL+F` stačí zadat IP a zbytek "proklikat").

## Použití v terminálu Linuxu:

```bash
$ sudo apt-get install ftp

$ ftp 192.168.x.x
ftp> ls
...
ftp> mput *.py
...
ftp> prompt
```

---

Zdrojová knihovna 🡒 [github.com/robert-hh/FTP-Server...](https://github.com/robert-hh/FTP-Server-for-ESP8266-ESP32-and-PYBD)

Možnost běhu i v threadu a pod., zatím netestováno.

```python
import uftpd
uftpd.start()
# uftpd.start([port = 21][, verbose = level])
```

---

Hezká ukázka použití:
https://www.youtube.com/watch?v=a7DrFqqu-78&t=369s

---
