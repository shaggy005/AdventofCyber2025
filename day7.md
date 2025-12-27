# Network Discovery - Scan-ta Clause

## What evil message do you see on top of the website?
<img width="351" height="175" alt="image" src="https://github.com/user-attachments/assets/c6b71a09-d6a0-4e5d-9e41-234bce745611" />

```
Pwned by HopSec
```
## What is the first key part found on the FTP server?
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
3aster_
```
## What is the second key part found in the TBFC app?
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
```
15_th3_
```
## What is the third key part found in the DNS records?
```
┌──(shaggy㉿kali)-[~]
└─$ nmap -sU 10.49.191.61
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-27 23:48 IST
Nmap scan report for 10.49.191.61
Host is up (0.042s latency).
Not shown: 999 open|filtered udp ports (no-response)
PORT   STATE SERVICE
53/udp open  domain

Nmap done: 1 IP address (1 host up) scanned in 43.27 seconds
                                                                              
┌──(shaggy㉿kali)-[~]
└─$ dig @10.49.191.61 TXT key3.tbfc.local +short
"KEY3:n3w_xm45"
```
```
n3w_xm45
```
## Which port was the MySQL database running on?
```
tbfcapp@tbfc-devqa01:~$ ss -tunlp                                                                                         
Netid       State        Recv-Q        Send-Q                   Local Address:Port                Peer Address:Port       
Process                                                                                                                   
udp         UNCONN       0             0                              0.0.0.0:53                       0.0.0.0:*          


udp         UNCONN       0             0                    10.49.191.61%ens5:68                       0.0.0.0:*          


tcp         LISTEN       0             511                            0.0.0.0:80                       0.0.0.0:*          


tcp         LISTEN       0             32                             0.0.0.0:53                       0.0.0.0:*          


tcp         LISTEN       0             151                          127.0.0.1:3306                     0.0.0.0:*          


tcp         LISTEN       0             4096                           0.0.0.0:22                       0.0.0.0:*          


tcp         LISTEN       0             4096                         127.0.0.1:7681                     0.0.0.0:*          


tcp         LISTEN       0             32                             0.0.0.0:21212                    0.0.0.0:*          


tcp         LISTEN       0             50                             0.0.0.0:25251                    0.0.0.0:*          


tcp         LISTEN       0             2048                         127.0.0.1:8000                     0.0.0.0:*          
 users:(("gunicorn",pid=973,fd=5),("gunicorn",pid=967,fd=5),("gunicorn",pid=681,fd=5))                                    
tcp         LISTEN       0             4096                              [::]:22                          [::]:*          


tbfcapp@tbfc-devqa01:~$                                                                                                   
```
- 3306 is the default mysql port
```
3306
```
## Finally, what's the flag you found in the database?
```
tbfcapp@tbfc-devqa01:~$ mysql -D tbfcqa01 -e "show tables;"                                                               
+--------------------+                                                                                                    
| Tables_in_tbfcqa01 |                                                                                                    
+--------------------+                                                                                                    
| flags              |                                                                                                    
+--------------------+                                                                                                    
tbfcapp@tbfc-devqa01:~$ mysql -D tbfcqa01 -e "select * from flags;"                                                       
+----+------------------------------+                                                                                     
| id | flag                         |                                                                                     
+----+------------------------------+                                                                                     
|  1 | THM{4ll_s3rvice5_d1sc0vered} |                                                                                     
+----+------------------------------+                                                                                     
tbfcapp@tbfc-devqa01:~$
```

```
THM{4ll_s3rvice5_d1sc0vered}
```
