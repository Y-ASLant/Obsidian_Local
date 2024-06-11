# 树莓派操作系统烧录

工具：etcher    
镜像：Raspbian Buster、Kali Linux RaspberryPi

> [!ERROR] | [Etcher工具](https://www.balena.io/etcher/) | [树莓派镜像](https://www.raspberrypi.org/downloads/raspbian/) | [Kali for 树莓派](https://www.offensive-security.com/kali-linux-arm-images/) |
  解压后，使用etcher将镜像烧录进SD卡，等待烧录完成接入主板。

  下面针对不同的系统，解决树莓派上网、访问、更新源等问题。

## 树莓派安装raspberry

### 如何配置联网

  烧录完成后，暂不拔出SD卡，会发现电脑多了一个分区boot分区。

  新建文件wpa_supplicant.conf

  内容为：

```shell
  country=CN
  ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
  update_config=1
  network={
  ssid="WiFi-A"
  psk="12345678"
  key_mgmt=WPA-PSK
  priority=1
  }
```
### 如何发现树莓派的IP地址
先使用fping发现自己电脑网段里面存活的主机IP
```shell

fping -ag 192.168.1.0/24 > ip_alive.txt

```

-a 是alive的意思

-g 是扫描网段

再用nmap扫描这些IP的ssh端口（22）

File: scan.sh
```shell
IP_LIST=$(cat iplist.txt)
for IP in $IP_LIST
do
nmap -sT -p 22 $IP
done
```

一般主机不会开放22端口，所以22为open的IP就是树莓派的IP
或者：
直接进入路由器的管理界面查看树莓派设备的IP地址。

### 如何配置ssh登录

在boot分区下新建一个文件名为SSH，注意大写。

然后加电，可以通过用户名pi密码raspberry。
## 树莓派安装kali
### 如何配置联网，
- 如何发现树莓派的IP地址

  先使用fping发现自己电脑网段里面存活的主机IP

  

复制

  

```shell

fping -ag 192.168.1.0/24 > ip_alive.txt

```

  

-a 是alive的意思

-g 是扫描网段

再用nmap扫描这些IP的ssh端口（22）

File: scan.sh

  

```shell

IP_LIST=$(cat iplist.txt)

for IP in $IP_LIST

do

nmap -sT -p 22 $IP

done

```

一般主机不会开放22端口，所以22为open的IP就是树莓派的IP

或者：

直接进入路由器的管理界面查看树莓派设备的IP地址。

加电，用户名root密码toor

遇到问题拔掉网线后，无线网卡会拿不到IP地址。

```shell

ifconfig -a

vim /etc/network/interfaces

```

```shell

auto lo

iface lo inet dhcp

  

auto eth0

iface eth0 inet dhcp

  

auto wlan0

iface wlan0 inet dhcp

wpa-ssid TP-LINK_A686

wpa-psk 123456.#!A

```

### 修改源：

```shell

deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

```

参考链接：https://www.jianshu.com/p/3497c4a7f417
### 安装远程桌面

```shell

apt-get install tightvncserver

tightvncserver

```

参考链接：https://www.cnblogs.com/jokermoon/p/6746702.html
设置远程连接密码。然后ip:1输入刚设置的密码roottoor

### 更新为完整版的Kali Linux

```shell
apt-get update
apt-get updgrade -y
apt-get install kali-linux-full -y
```