### Hack the Box - Mischief Writeup
> 國防大學理工學院資工系 廖耕樺
> 
> Ref to: https://0xdf.gitlab.io/2020/06/30/htb-blocky.html

### 說明資訊

* 來源：Hack the box
* 作業系統：Linux
* 靶機發佈日期： 21 Jul 2017
* 難度：Easy

### 作業步驟

#### 情蒐階段
```bash
─[sg-vip-1]─[10.10.14.38]─[alohaski@htb-kgeekjo0ns]─[~]
└──╼ [★]$ sudo nmap -p- -sC -sV 10.10.10.37 -T5
Starting Nmap 7.93 ( https://nmap.org ) at 2023-12-25 16:13 GMT
Nmap scan report for 10.10.10.37
Host is up (0.31s latency).
Not shown: 65530 filtered tcp ports (no-response)
PORT      STATE  SERVICE   VERSION
21/tcp    open   ftp       ProFTPD 1.3.5a
22/tcp    open   ssh       OpenSSH 7.2p2 Ubuntu 4ubuntu2.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 d62b99b4d5e753ce2bfcb5d79d79fba2 (RSA)
|   256 5d7f389570c9beac67a01e86e7978403 (ECDSA)
|_  256 09d5c204951a90ef87562597df837067 (ED25519)
80/tcp    open   http      Apache httpd 2.4.18
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Did not follow redirect to http://blocky.htb
8192/tcp  closed sophos
25565/tcp open   minecraft Minecraft 1.11.2 (Protocol: 127, Message: A Minecraft Server, Users: 0/20)
Service Info: Host: 127.0.1.1; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 337.17 seconds
```
* 發現21 port 有開，但無法正確登入
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/af12aa53-ac41-41e1-bff5-f06d7cf3b32d)
* 80 port有開，http server，成功進入網站
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/dde465b5-4e84-4571-86d0-5eb98de47fc1)
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/5a4c75c7-8560-483a-a4a7-1dc944d82473)
* 注意到他給的hint :wordpass
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/71078285-72dc-4dd0-a08f-4076c96ccf4c)

```bash
┌──(root㉿kali)-[/home/kali]
└─# wpscan --url http://blocky.htb -e u
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.25
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://blocky.htb/ [10.10.10.37]
[+] Started: Mon Dec 25 12:18:31 2023
```
* 找到user
  
  ![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/1d01e61d-02de-4298-ba4f-c77263671c6f)

```bash
──(root㉿kali)-[/home/kali]
└─# apt update && apt install -y feroxbuster
```
💣feroxbuster Introduction💣
---
**feroxbuster** is a tool designed to perform Forced Browsing.

Forced browsing is an attack where the aim is to enumerate and access resources that are not referenced by the web application, but are still accessible by an attacker.

feroxbuster uses brute force combined with a wordlist to search for unlinked content in target directories. These resources may store sensitive information about web applications and operational systems, such as source code, credentials, internal network addressing, etc...

This attack is also known as Predictable Resource Location, File Enumeration, Directory Enumeration, and Resource Enumeration.
#### 網站爆破
```bash
┌──(root㉿kali)-[/home/kali]
└─# feroxbuster --url http://blocky.htb -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -C 404 -n 

 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.10.1
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://blocky.htb
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
 💢  Status Code Filters   │ [404]
 💥  Timeout (secs)        │ 7
 🦡  User-Agent            │ feroxbuster/2.10.1
 💉  Config File           │ /etc/feroxbuster/ferox-config.toml
 🔎  Extract Links         │ true
 🏁  HTTP methods          │ [GET]
 🚫  Do Not Recurse        │ true
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Management Menu™
```
* -C 404 filters out pages that return the HTTP status code 404.
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/e054cc63-dac2-477d-8ef2-fd80af49d458)
* /wiki
  ![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/379c5362-5d30-492b-8f90-c3c5723101e1)

* /plugins
  ![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/6774006b-bb01-465a-9424-9df5ee23e89e)
  >發現路徑下，有2個檔案
![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/5a04e208-9171-480f-b078-841bdab0b932)
  >>發現root 

* /phpmyadmin

#### 連線
* 透過剛剛蒐集的user-Notch，用ssh 連線
  * user:notch
  * password:8YsqfCTnvxAUeduzjNSXe22\

![image](https://github.com/Draw0919/Pub-ClassWork/assets/102810421/33ab8145-7f68-41c0-af48-7fec6110cf31)

> ROOT👍
>> 9c21d2918807e41fa01201acb11ee997


  








