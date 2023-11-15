# msf免杀

## 实验环境

Kali  192.168.195.128

![1700034625033](D:\作业\Linux\msf免杀\img\1.png)

Winser2008  192.168.195.129

![2](D:\作业\Linux\msf免杀\img\2.png)

## 实验步骤

#### 启动postgresql.service

```bash
systemctl restart postgresql.service
```

#### 启动msf

```basic
msfconsole
```

#### 使用模块拿到Winser2008的shell

![3](D:\作业\Linux\msf免杀\img\3.png)

![1700034758825](D:\作业\Linux\msf免杀\img\4.png)

![1700034884455](D:\作业\Linux\msf免杀\img\5.png)

![1700034979961](D:\作业\Linux\msf免杀\img\6.png)

![1700035064095](D:\作业\Linux\msf免杀\img\7.png)

![1700035114111](D:\作业\Linux\msf免杀\img\8.png)

#### 制作伪装木马

![1700035490652](D:\作业\Linux\msf免杀\img\9.png)

#### 使用监听模块

![1700035765430](D:\作业\Linux\msf免杀\img\10.png)

#### 使用上传模块

![1700035842788](D:\作业\Linux\msf免杀\img\11.png)

![1700036081995](D:\作业\Linux\msf免杀\img\12.png)

## 验证

![1700036142310](D:\作业\Linux\msf免杀\img\13.png)