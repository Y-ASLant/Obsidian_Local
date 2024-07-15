## 打开 SSH 端口 

> [!BUG] ssh 默认端口号为 22
 
```sh
# 以root身份执行！否则是空白文件
su

# 打开配置文件
vi /etc/ssh/sshd_config

# 进入编辑模式
i

# 手动将#Port 22中的#去掉

# 保存并退出（按Esc后输入）
:wq

# 重启sshd服务
service sshd restart
# 或
systemctl restart sshd
# Ubuntu：
sudo service ssh restart
```

> [!BUG] 本站点公网 IP : 4x.1xx.13.41

## 通过 Windows 自带终端进行连接

1. Win + R 弹出运行
2. 输入 PowerShell 
3. 回车进入

> [!tip] 格式：

```sh
ssh 用户名@公网 IP 
```

> [!success] 输入密码即可连接

```shell
PS C:\Users\ASLan> ssh root@4x.1xx.13.41
root@47.120.13.41's password:
Last failed login: Tue May 14 12:27:18 CST 2024 from 47.108.193.65 on ssh:notty
There were 51 failed login attempts since the last successful login.
Last login: Sun May 12 22:21:15 2024 from 113.128.199.194

Welcome to Alibaba Cloud Elastic Compute Service !

[root@ASLant ~]#
```

## 安装 neofetch

```zsh
# 1. 安装 epel-release
sudo yum install epel-release

# 2.添加第三方软件源
curl -o /etc/yum.repos.d/konimex-neofetch-epel-7.repo https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo

# 3.使用包管理器安装 neofetch
sudo yum install neofetch
```

```sh
[root@ASLant ~]# neofetch
                 ..                    root@ASLant
               .PLTJ.                  -----------
              <><><><>                 OS: CentOS Linux release 7.9.2009 (Core) x86_64
     KKSSV' 4KKK LJ KKKL.'VSSKK        Host: Alibaba Cloud ECS pc-i440fx-2.1
     KKV' 4KKKKK LJ KKKKAL 'VKK        Kernel: 3.10.0-1160.105.1.el7.x86_64
     V' ' 'VKKKK LJ KKKKV' ' 'V        Uptime: 217 days, 18 hours, 27 mins
     .4MA.' 'VKK LJ KKV' '.4Mb.        Packages: 618 (rpm)
   . KKKKKA.' 'V LJ V' '.4KKKKK .      Shell: bash 4.2.46
 .4D KKKKKKKA.'' LJ ''.4KKKKKKK FA.    Terminal: /dev/pts/0
<QDD ++++++++++++  ++++++++++++ GFD>   CPU: Intel Xeon Platinum (4) @ 2.500GHz
 'VD KKKKKKKK'.. LJ ..'KKKKKKKK FV     GPU: 00:02.0 Cirrus Logic GD 5446
   ' VKKKKK'. .4 LJ K. .'KKKKKV '      Memory: 1069MiB / 4096MiB
      'VK'. .4KK LJ KKA. .'KV'
     A. . .4KKKK LJ KKKKA. . .4
     KKA. 'KKKKK LJ KKKKK' .4KK
     KKSSA. VKKK LJ KKKV .4SSKK
              <><><><>
               'MKKM'
                 ''

[root@ASLant ~]#
```

## 使用官方提供的 SSH 工具进行连接

![[../ASLant_Files/68002362f780da61ff47a2e0e59447e5_MD5.jpg]]

## 通过 Xshell 等第三方工具进行连接

> [!success]- Download
> [Xshell]()
> [Xftp]()

 ![[../ASLant_Files/58185241dcb30486c77f494acfc09c12_MD5.jpg]]