# Kali ettercap DNS欺骗

## 实验环境

Kali  IP:192.168.195.128  

![1](D:\作业\Linux\Kali ettercap DNS欺骗\img\1.png)

gateway  192.168.195.2

![1698820810851](D:\作业\Linux\Kali ettercap DNS欺骗\img\2.png)

Winser2008R2   IP:192.168.195.129     gateway:192.168.195.2

![1698820920819](D:\作业\Linux\Kali ettercap DNS欺骗\img\3.png)

网络互通：Winser2008R2   ping   kali

![1698821019075](D:\作业\Linux\Kali ettercap DNS欺骗\img\4.png)

网络互通：kali  ping   Winser2008R2

![1698821085915](D:\作业\Linux\Kali ettercap DNS欺骗\img\5.png)

## 实验步骤

#### 修改ettercap解析文件

```basic
vim /etc/ettercap/etter.dns  
```

![1698821289476](D:\作业\Linux\Kali ettercap DNS欺骗\img\6.png)

#### apache服务

```basic
启动apache服务
┌──(root💀kali)-[/var/www/html]
└─# systemctl start apache2 

查看apache服务
┌──(root💀kali)-[/var/www/html]
└─# systemctl status apache2
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor p>
     Active: active (running) since Wed 2023-11-01 14:12:51 CST; 36min ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 1772 ExecStart=/usr/sbin/apachectl start (code=exited, status=>
   Main PID: 1783 (apache2)
      Tasks: 6 (limit: 4915)
     Memory: 15.1M
     CGroup: /system.slice/apache2.service
             ├─1783 /usr/sbin/apache2 -k start
             ├─1785 /usr/sbin/apache2 -k start
             ├─1786 /usr/sbin/apache2 -k start
             ├─1787 /usr/sbin/apache2 -k start
             ├─1788 /usr/sbin/apache2 -k start
             └─1789 /usr/sbin/apache2 -k start

11月 01 14:12:51 kali systemd[1]: Starting The Apache HTTP Server...
11月 01 14:12:51 kali apachectl[1782]: AH00558: apache2: Could not reliably>
11月 01 14:12:51 kali systemd[1]: Started The Apache HTTP Server.
```

#### ettercap

```basic
图形化启动ettercap
┌──(root💀kali)-[/var/www/html]
└─# ettercap -G      
```

![1698821612547](D:\作业\Linux\Kali ettercap DNS欺骗\img\7.png)

![1698821828427](D:\作业\Linux\Kali ettercap DNS欺骗\img\8.png)

![1698821994995](D:\作业\Linux\Kali ettercap DNS欺骗\img\9.png)

##### 选择ARP攻击

![1698822060315](D:\作业\Linux\Kali ettercap DNS欺骗\img\10.png)

![1698822095180](D:\作业\Linux\Kali ettercap DNS欺骗\img\11.png)

##### 选择DNS欺骗攻击插件

![1698822271587](D:\作业\Linux\Kali ettercap DNS欺骗\img\12.png)

## 验证

打开Winser2008R2，在IE中搜索http://www.baidu.com

![image-20231101205158635](D:\作业\Linux\Kali ettercap DNS欺骗\img\13.png)

发现百度的页面变为Apache的默认页面，DNS欺骗成功