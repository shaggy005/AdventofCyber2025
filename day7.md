# Network Discovery - Scan-ta Clause

```
┌──(shaggy㉿kali)-[~]
└─$ ftp 10.49.191.61 21212
Connected to 10.49.191.61.
220 (vsFTPd 3.0.5)
Name (10.49.191.61:shaggy): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||55857|)
ftp: Can't connect to `10.49.191.61:55857': Connection timed out
200 EPRT command successful. Consider using EPSV.
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            13 Oct 22 16:27 tbfc_qa_key1
226 Directory send OK.
ftp> get tbfc_qa_key1 -
remote: tbfc_qa_key1
200 EPRT command successful. Consider using EPSV.
150 Opening BINARY mode data connection for tbfc_qa_key1 (13 bytes).
KEY1:3aster_
226 Transfer complete.
13 bytes received in 00:00 (0.30 KiB/s)
ftp> 
```
```
┌──(shaggy㉿kali)-[~]
└─$ nc -v 10.49.191.61 25251
10.49.191.61: inverse host lookup failed: Unknown host
(UNKNOWN) [10.49.191.61] 25251 (?) open
TBFC maintd v0.2
Type HELP for commands.
HELP
Commands: HELP, STATUS, GET KEY, QUIT
GET KEY
KEY2:15_th3_
```
